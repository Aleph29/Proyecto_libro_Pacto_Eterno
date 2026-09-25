# Si diereis oído a mi voz — sitio del plan del libro

Sitio estático (HTML puro, sin dependencias de compilación) con tres páginas:

- `index.html` — Plan del libro
- `pendientes.html` — Pendientes del libro
- `diagrama.html` — Mapa de hilos temáticos

Generado a partir del Plan del libro y los Pendientes del libro en Claude. Para actualizarlo, vuelve a pedirle a Claude que regenere el sitio cuando el documento cambie, o edita el HTML directamente.

## 1. Subirlo a GitHub

No tengo acceso a tu cuenta de GitHub, así que estos pasos los haces tú. Necesitas [Git](https://git-scm.com/downloads) instalado y una cuenta de GitHub.

**Opción A — desde la terminal:**

```bash
cd ruta/a/esta/carpeta
git init
git add .
git commit -m "Sitio del plan del libro"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/NOMBRE-DEL-REPO.git
git push -u origin main
```

Antes de la última línea, crea el repositorio vacío en GitHub: entra a [github.com/new](https://github.com/new), ponle un nombre (por ejemplo `plan-del-libro`), no marques "Add a README" (ya tienes uno) y da clic en **Create repository**. Copia la URL que te muestra GitHub y úsala en el `git remote add origin`.

**Opción B — sin terminal:** entra a [github.com/new](https://github.com/new), crea el repositorio, y en la página del repositorio usa **uploading an existing file** para arrastrar los archivos de esta carpeta (`index.html`, `pendientes.html`, `diagrama.html`, `vercel.json`, `README.md`).

## 2. Publicarlo en Vercel

1. Entra a [vercel.com](https://vercel.com) e inicia sesión con tu cuenta de GitHub (si no tienes cuenta de Vercel, "Continue with GitHub" crea una).
2. Clic en **Add New… → Project**.
3. Elige el repositorio que acabas de crear (Vercel pedirá permiso para acceder a tus repos la primera vez).
4. Framework Preset: déjalo en **Other** (es un sitio estático, no hace falta build). No necesitas cambiar nada más.
5. Clic en **Deploy**. En menos de un minuto tendrás una URL como `https://plan-del-libro.vercel.app`.

Desde ese momento, **cada vez que subas cambios a la rama `main` de GitHub, Vercel vuelve a publicar el sitio automáticamente**, sin que tengas que repetir estos pasos.

## 3. Actualizarlo más adelante

Cuando el Plan del libro o los Pendientes cambien:

1. Pide a Claude que regenere los archivos HTML (o pídele el mismo prompt: "actualiza la página web con el plan del libro").
2. Reemplaza los archivos en esta carpeta.
3. Sube los cambios:
   ```bash
   git add .
   git commit -m "Actualiza el plan del libro"
   git push
   ```
4. Vercel lo publica solo.

## Notas

- El sitio no tiene backend ni base de datos: es HTML y CSS puros, con tipografías de Google Fonts (Fraunces y Source Serif 4) cargadas por enlace.
- Es privado en el sentido de que solo quien tenga la URL de Vercel puede verlo; si quieres protegerlo con contraseña, Vercel lo permite en los planes de pago (Password Protection, en la configuración del proyecto).
- Si prefieres un dominio propio (por ejemplo `tulibronombre.com`), se agrega desde el panel del proyecto en Vercel, en **Settings → Domains**.
