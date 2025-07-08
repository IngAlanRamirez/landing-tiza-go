# 🚀 Deployment Guide - Tiza Go Landing

## 📋 Available Deployment Methods

### 1. **Automatic GitHub Pages (Recommended)**

- **Branch**: `main`
- **Trigger**: Automático en cada push a `main`
- **URL**: https://ingalanramirez.github.io/landing-tiza-go/
- **Time**: 2-3 minutos

### 2. **Manual GitHub Actions Trigger**

```bash
# Forzar deployment con commit vacío
bun run deploy:force
```

### 3. **Direct gh-pages Deploy**

```bash
# Deploy directo usando gh-pages
bun run deploy
```

## 🔧 Setup Commands

### First Time Setup

```bash
# Install dependencies
bun install

# Build and test locally
bun run build
bun run preview
```

### Regular Deployment Workflow

```bash
# 1. Make changes on develop
git checkout develop
# ... make changes ...
git add . && git commit -m "feat: new feature"
git push origin develop

# 2. Merge to main and deploy
git checkout main
git merge develop
git push origin main  # This triggers automatic deployment
```

## 📊 Deployment Status

- **GitHub Actions**: ✅ Configured
- **GitHub Pages**: ✅ Enabled
- **Custom Domain**: ❌ Not configured
- **HTTPS**: ✅ Enabled by default

## 🔗 Links

- **Live Site**: https://ingalanramirez.github.io/landing-tiza-go/
- **Repository**: https://github.com/IngAlanRamirez/landing-tiza-go
- **Actions**: https://github.com/IngAlanRamirez/landing-tiza-go/actions

## 🚨 Troubleshooting

### If deployment fails:

1. Check GitHub Actions logs
2. Verify package.json scripts
3. Run `bun run build` locally to test
4. Use `bun run deploy` as fallback

### If site doesn't update:

1. Clear browser cache
2. Check if workflow completed
3. Verify GitHub Pages settings
4. Try manual deployment

---

**Last Updated**: December 2024
**Deployment Method**: GitHub Actions + GitHub Pages
**Build Tool**: Astro + Bun
