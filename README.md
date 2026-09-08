# ALMA Home & Style

Tienda web de **Andrea López Mezone** — moda y artículos para el hogar importados:
suéteres y tejidos, edredones, licras, esquineros y más.

Sitio estático de una sola página (HTML + [Tailwind CSS](https://tailwindcss.com/) vía CDN +
[Font Awesome](https://fontawesome.com/)), sin build ni dependencias que instalar.

## 🌐 Ver el sitio

👉 **https://alma-home-style.onrender.com/**

## 📁 Estructura

```
.
├── index.html      # La página completa: maquetación, catálogo de productos y lógica JS
├── 404.html        # Página de error personalizada
├── .nojekyll       # Sin efecto en Render; se conserva por compatibilidad
├── .gitignore
└── *.jpg           # Fotos de productos (ver «Imágenes» más abajo)
```

## 🖼️ Imágenes de productos

Cada producto en `index.html` define dos imágenes:

```js
localImage:    "127515.jpg",                        // foto real, en la raíz del repo
fallbackImage: "https://images.unsplash.com/...",   // se usa si la local no existe
```

Los archivos `127489.jpg`, `127505.jpg`, `127507.jpg`, `127509.jpg`, `127511.jpg`,
`127513.jpg`, `127515.jpg` y `127517.jpg` **no están en el repo todavía**. Mientras falten,
la web muestra automáticamente las fotos de respaldo de Unsplash. Para usar las fotos reales,
copia esos `.jpg` en la raíz del proyecto y haz commit.

## ✏️ Cómo editar el catálogo

Los productos viven en el array `products` dentro de `index.html` (busca `const products = [`).
Para añadir uno nuevo, copia un bloque completo y cambia sus campos:

```js
{
    id: 110,
    name: "Nombre del producto",
    category: "damas-tejidos",                 // debe coincidir con una categoría existente
    categoryLabel: "Suéteres & Tejidos Importados",
    price: 38.00,
    badge: "✨ Tendencia 2026",
    localImage: "mi-foto.jpg",
    fallbackImage: "https://...",
    desc: "Descripción corta del producto.",
    colors: ["Blanco Marfil", "Negro"],
    sizes: ["Talla Única Estándar (S - L)"]
}
```

## ✅ Pendientes

- [ ] Reemplazar el número de WhatsApp de ejemplo `51900000000` por el real
      (aparece 5 veces en `index.html`).
- [ ] Añadir las fotos `.jpg` de los productos (ver «Imágenes» arriba).
- [x] ~~Publicar la web (Render).~~
- [x] ~~Poner la URL real en `canonical`, `og:url` y este README.~~

## 🚀 Publicación

El sitio se sirve desde **Render** como *Static Site*, conectado a este repositorio:

- Web: https://alma-home-style.onrender.com/
- Repositorio: https://github.com/cmezone60-ctrl/alma-home-style

Configuración del servicio en Render:

| Ajuste | Valor |
| --- | --- |
| Tipo | Static Site |
| Branch | `main` |
| Build Command | *(vacío)* |
| Publish Directory | `.` |
| Auto-Deploy | **Off** (los despliegues son manuales) |
| Rewrite | `/*` → `/404.html` |

## 🔄 Actualizar la web

Como el auto-deploy está desactivado, publicar son **dos pasos separados**:

```bash
# 1. Guardar los cambios en GitHub (no toca la web en vivo)
git add -A
git commit -m "Actualizo el catálogo"
git push

# 2. Publicar en Render (dispara el despliegue)
curl "$(cat ~/.alma-render-hook.txt)"
```

> 🔐 El *deploy hook* es **secreto** y vive en `C:\Users\cmezo\.alma-render-hook.txt`,
> deliberadamente **fuera del repositorio**. No debe subirse nunca a GitHub.

## 💻 Ver en local

Abre `index.html` con doble clic, o levanta un servidor local:

```bash
python -m http.server 8000
# luego abre http://localhost:8000
```

---

© ALMA Home & Style — Andrea López Mezone
