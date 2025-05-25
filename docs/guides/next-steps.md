# Next Steps - Do and Done Project

## Immediate Actions Required

### 1. Install Workspace Dependencies

```bash
# This will install all dependencies for all workspaces
pnpm install
```

### 2. Create Backend Structure

#### Create Prisma Schema

Create `backend/prisma/schema.prisma`:

```prisma
// This is your Prisma schema file
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id        String   @id @default(cuid())
  email     String   @unique
  password  String
  name      String?
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```

#### Create Backend Entry Point

Create `backend/src/index.ts`:

```typescript
import express from 'express';
import cors from 'cors';
import helmet from 'helmet';
import dotenv from 'dotenv';

dotenv.config();

const app = express();
const PORT = process.env.PORT || 3000;

app.use(helmet());
app.use(cors());
app.use(express.json());

app.get('/health', (req, res) => {
  res.json({ status: 'ok', timestamp: new Date().toISOString() });
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

### 3. Create Web Structure

#### Create Vite Config

Create `web/vite.config.ts`:

```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  server: {
    port: 5173,
    proxy: {
      '/api': {
        target: 'http://localhost:3000',
        changeOrigin: true,
      },
    },
  },
});
```

#### Create Web Entry Files

Create `web/index.html`:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Do and Done</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

Create `web/src/main.tsx`:

```typescript
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <div>Hello Do and Done!</div>
  </React.StrictMode>
);
```

### 4. Development Workflow

Once the above files are created:

1. **Start Docker services:**

   ```bash
   docker-compose up -d
   ```

2. **Copy environment file:**

   ```bash
   cp backend/.env.example backend/.env
   ```

3. **Run database migrations:**

   ```bash
   cd backend
   pnpm prisma:generate
   pnpm prisma:migrate
   ```

4. **Start development servers:**

   ```bash
   # In one terminal
   pnpm backend:dev

   # In another terminal
   pnpm web:dev
   ```

## Priority Order

1. **Week 1 Focus:**

   - Install all dependencies
   - Get backend server running
   - Get web app running
   - Implement basic authentication

2. **Week 2 Focus:**

   - Create task CRUD APIs
   - Build basic UI components
   - Connect frontend to backend

3. **Week 3-4 Focus:**
   - Add activity logging
   - Implement planned vs actual tracking
   - Create mobile app structure

## Common Issues & Solutions

### Issue: Dependencies fail to install

**Solution:** Clear cache and reinstall

```bash
pnpm store prune
rm -rf node_modules pnpm-lock.yaml
pnpm install
```

### Issue: Database connection fails

**Solution:** Ensure Docker is running

```bash
docker-compose ps
docker-compose restart postgres
```

### Issue: Port already in use

**Solution:** Change ports in configuration or kill existing process

```bash
lsof -i :3000  # Find process
kill -9 <PID>  # Kill process
```

---

**Remember:** Focus on getting a working MVP first, then iterate!
