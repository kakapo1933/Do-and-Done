# Do and Done - Productivity Tracking App

A productivity application that tracks both planned tasks and actual activities, helping users understand the gap between intentions and reality.

## 🚀 Project Status

Currently in **Phase 1: MVP Development**

## 📁 Project Structure

```
do-and-done/
├── backend/          # Node.js API server
├── mobile/           # Flutter mobile app (iOS/Android)
├── web/              # React web application
├── docs/             # Project documentation
│   ├── guides/       # Development guides
│   └── project-setup-log.md
├── .gitignore
├── CLAUDE.md         # AI assistant guidelines
└── README.md         # This file
```

## 🛠️ Technology Stack

### Frontend
- **Web**: React + TypeScript + Vite, Tailwind CSS
- **Mobile**: Flutter for iOS/Android
- **Package Manager**: pnpm

### Backend
- **API**: Node.js + Express/Fastify
- **Database**: PostgreSQL + Prisma ORM
- **Auth**: JWT + refresh tokens
- **Cache**: Redis

### Infrastructure
- **Containerization**: Docker + Docker Compose
- **Cloud**: AWS (planned)
- **CI/CD**: GitHub Actions (planned)

## 📋 Development Setup

### Prerequisites Installed
- ✅ Node.js v22.14.0
- ✅ pnpm v10.11.0
- ✅ Docker v28.0.4
- ✅ PostgreSQL client v17.4
- ⏳ Flutter SDK (pending installation)

### Quick Start

1. Clone the repository
```bash
git clone <repository-url>
cd do-and-done
```

2. Switch to development branch
```bash
git checkout develop
```

3. Install dependencies (once project is initialized)
```bash
# Backend
cd backend && pnpm install

# Web
cd ../web && pnpm install

# Mobile
cd ../mobile && flutter pub get
```

## 📚 Documentation

- [Technical Requirements](docs/guides/concept.md)
- [Development Plan](docs/guides/development-plan.md)
- [Quick Start Checklist](docs/guides/quick-start-checklist.md)
- [Project Setup Log](docs/project-setup-log.md)

## 🤝 Contributing

Please read [CLAUDE.md](CLAUDE.md) for development guidelines and coding standards.

## 📄 License

This project is currently private. License to be determined.