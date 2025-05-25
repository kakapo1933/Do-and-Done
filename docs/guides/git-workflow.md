# Git Workflow Guide

## Branch Strategy

### Main Branches

- `main` - Production-ready code (protected)
- `develop` - Integration branch for features

### Feature Branches

- `feature/*` - New features and enhancements
- `fix/*` - Bug fixes
- `chore/*` - Maintenance tasks
- `docs/*` - Documentation updates

## Workflow Rules

1. **Never commit directly to main or develop**
2. **Always create a feature branch** for any work
3. **Use descriptive branch names**
4. **Create pull requests** for code review

## Creating a Feature Branch

```bash
# From develop branch
git checkout develop
git pull origin develop
git checkout -b feature/your-feature-name

# Make changes
git add .
git commit -m "feat: Your descriptive message"

# Push to remote
git push -u origin feature/your-feature-name
```

## Commit Message Format

Follow conventional commits:

- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation changes
- `chore:` Maintenance tasks
- `test:` Test additions/changes
- `refactor:` Code refactoring

## Pull Request Process

1. Push feature branch to GitHub
2. Create pull request to `develop`
3. Request code review
4. Address feedback
5. Merge after approval

## Example Workflow

```bash
# Start new feature
git checkout develop
git pull origin develop
git checkout -b feature/add-authentication

# Work on feature
# ... make changes ...
git add .
git commit -m "feat: Add JWT authentication to backend"

# Push and create PR
git push -u origin feature/add-authentication
# Go to GitHub and create pull request
```

---

**Important:** This workflow ensures code quality and prevents direct commits to
protected branches.
