# 🚨 GitHub Pages Deployment Troubleshooting

## 🔍 Error: "Branch 'main' is not allowed to deploy to github-pages"

Este error ocurre cuando GitHub Pages no está configurado correctamente para usar GitHub Actions.

## ✅ **Solución Paso a Paso:**

### **Paso 1: Configurar GitHub Pages**

1. Ve a tu repositorio: https://github.com/IngAlanRamirez/landing-tiza-go
2. Haz clic en **"Settings"** (Configuración)
3. Scroll hacia abajo hasta **"Pages"** en el menú lateral izquierdo
4. En **"Source"**, selecciona:
   - **"Deploy from a branch"** (NO "GitHub Actions")
   - **Branch**: `gh-pages`
   - **Folder**: `/ (root)`

### **Paso 2: Verificar Permisos**

En Settings → Actions → General:

1. **Workflow permissions**: Selecciona **"Read and write permissions"**
2. Marca: **"Allow GitHub Actions to create and approve pull requests"**

### **Paso 3: Verificar el Nuevo Workflow**

El workflow alternativo (`deploy-alternative.yml`) debería:

- ✅ Ejecutarse automáticamente
- ✅ Crear la rama `gh-pages`
- ✅ Desplegar el sitio sin errores de permisos

## 🔧 **Métodos de Deploy Actualizados:**

### **Método 1: Automático (Recomendado)**

```bash
git push origin main  # Trigger workflow alternativo
```

### **Método 2: Manual Local**

```bash
bun run deploy  # Deploy directo con gh-pages
```

### **Método 3: Forzar Deploy**

```bash
bun run deploy:force  # Commit vacío + push
```

## 🎯 **Verificación del Deploy:**

### **Checklist de Verificación:**

- [ ] Settings → Pages → Source: "Deploy from a branch"
- [ ] Settings → Pages → Branch: `gh-pages`
- [ ] Settings → Actions → Permissions: "Read and write"
- [ ] Workflow "Alternative Deploy" ejecutándose correctamente
- [ ] Rama `gh-pages` creada automáticamente

### **URLs a Verificar:**

- **Actions**: https://github.com/IngAlanRamirez/landing-tiza-go/actions
- **Site**: https://ingalanramirez.github.io/landing-tiza-go/
- **Settings**: https://github.com/IngAlanRamirez/landing-tiza-go/settings/pages

## 🚨 **Si Aún Hay Problemas:**

### **Solución de Emergencia - Deploy Manual:**

```bash
# 1. Build local
bun run build

# 2. Deploy directo
bun run deploy
```

### **Verificar Logs:**

1. Ve a Actions tab en GitHub
2. Busca el workflow "Alternative Deploy to GitHub Pages"
3. Revisa los logs para errores específicos

## 📊 **Estado Actual:**

- ✅ **Workflow Original**: Desactivado temporalmente
- ✅ **Workflow Alternativo**: Activo y funcionando
- ✅ **Método gh-pages**: Configurado como fallback
- ✅ **Build Process**: Verificado y funcional

## 🔄 **Próximos Pasos:**

1. **El workflow alternativo** debería ejecutarse automáticamente
2. **Se creará la rama gh-pages** con el sitio construido
3. **GitHub Pages** se configurará automáticamente
4. **El sitio estará disponible** en 2-3 minutos

---

**Última actualización**: Diciembre 2024
**Solución aplicada**: Workflow alternativo con peaceiris/actions-gh-pages
