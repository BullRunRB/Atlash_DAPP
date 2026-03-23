# ATLASH DApp — Guía de despliegue

Este paquete contiene todo lo necesario para publicar la DApp de ATLASH
en cualquiera de las tres plataformas gratuitas. Solo necesitas un navegador.

---

## ⚡ Opción 1 — Netlify Drop (más fácil, 30 segundos)

1. Abre https://app.netlify.com/drop en tu navegador
2. **Arrastra esta carpeta completa** (`atlash-deploy/`) al área de drop
3. Netlify te da una URL pública instantánea, por ejemplo:
   `https://atlash-abc123.netlify.app`
4. *(Opcional)* Crea cuenta gratuita en Netlify para:
   - Cambiar la URL a algo como `https://atlash.netlify.app`
   - Re-desplegar fácilmente cuando actualices el archivo

> ✅ MetaMask funciona de inmediato bajo HTTPS.

---

## 🐙 Opción 2 — GitHub Pages (URL permanente y profesional)

### Paso a paso:

1. Ve a https://github.com y crea una cuenta si no tienes
2. Haz clic en **"New repository"**
3. Nombre del repo: `atlash-dapp` (o el que prefieras)
4. Marca **Public** y haz clic en **"Create repository"**
5. En la página del repo, haz clic en **"uploading an existing file"**
6. Arrastra los archivos de esta carpeta:
   - `index.html`
   - `netlify.toml` (opcional, ignorado por GitHub Pages)
   - `vercel.json` (opcional)
7. Haz clic en **"Commit changes"**
8. Ve a **Settings → Pages**
9. En "Source" selecciona **"Deploy from a branch"**
10. Branch: `main`, folder: `/ (root)` → **Save**
11. En ~1 minuto tu DApp estará en:
    `https://TU-USUARIO.github.io/atlash-dapp/`

> ✅ URL permanente. Puedes conectar un dominio propio (ej: `app.atlash.io`).

---

## 🔺 Opción 3 — Vercel (el más rápido con cuenta)

1. Ve a https://vercel.com y crea cuenta (puedes usar tu cuenta de GitHub)
2. Haz clic en **"Add New → Project"**
3. Importa el repositorio de GitHub que creaste en la Opción 2
   *— o —* usa el CLI: `npx vercel` en esta carpeta
4. Vercel detecta automáticamente la configuración (`vercel.json`)
5. Tu DApp queda en: `https://atlash-dapp.vercel.app`

> ✅ Deploy automático cada vez que hagas push al repo de GitHub.

---

## 🌐 Dominio propio (opcional)

Si tienes un dominio como `app.atlash.io`:

- **Netlify**: Settings → Domain management → Add custom domain
- **GitHub Pages**: Settings → Pages → Custom domain
- **Vercel**: Settings → Domains → Add

Todas las plataformas te guían para configurar los DNS (normalmente
es agregar un registro CNAME).

---

## 📋 Contenido de este paquete

| Archivo | Descripción |
|---|---|
| `index.html` | La DApp completa (todo en un solo archivo) |
| `netlify.toml` | Configuración de headers de seguridad para Netlify |
| `vercel.json` | Configuración para Vercel |
| `_headers` | Headers alternativos para GitHub Pages / Netlify |
| `README.md` | Esta guía |

---

## ❓ Preguntas frecuentes

**¿Por qué MetaMask no funciona si abro el HTML directo?**
MetaMask requiere HTTPS. Al abrir `index.html` directamente el protocolo
es `file://` y MetaMask no inyecta `window.ethereum` por seguridad.
Cualquiera de las opciones anteriores usa HTTPS automáticamente.

**¿Puedo actualizar la DApp después?**
Sí. Reemplaza el `index.html` y vuelve a subir. En GitHub Pages / Vercel
el deploy es automático al hacer push.

**¿Es seguro?**
La DApp solo hace lecturas RPC a BSC. No guarda contraseñas ni claves
privadas. La wallet nunca sale del navegador del usuario.
