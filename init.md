# Documentación como Código en GitHub
## Guía para publicar este sitio con GitHub Pages

Esta guía explica cómo desplegar el sitio web del curso en **GitHub Pages** de forma automática, de modo que cualquier cambio en el repositorio se refleje en la web en segundos.

---

## 1. Arquitectura y herramientas

| Componente | Rol |
|------------|-----|
| **GitHub Repository** | Almacenamiento central de los archivos HTML, CSS y Markdown |
| **HTML estático** | Sitio web generado directamente, sin build tools ni dependencias |
| **GitHub Actions** | Pipeline de CI/CD que publica el sitio automáticamente en cada push |
| **GitHub Pages** | Servicio de hosting gratuito incluido en GitHub que sirve el sitio |

---

## 2. Estructura del repositorio

```
doc-web/
├── index.html          ← Página de inicio
├── modulo1.html
├── modulo2.html
├── modulo3.html
├── modulo4.html
├── css/
│   └── style.css
├── INFO.md             ← Contenido del curso (fuente de verdad)
├── init.md             ← Esta guía
└── .github/
    └── workflows/
        └── pages.yml   ← Pipeline de publicación automática
```

---

## 3. Habilitar GitHub Pages (una sola vez)

1. Ir al repositorio en GitHub
2. Entrar a **Settings → Pages**
3. En **Source**, seleccionar **GitHub Actions**
4. Guardar

A partir de este momento, cada push al branch `main` disparará el pipeline y actualizará el sitio.

---

## 4. Pipeline de publicación automática

Crear el archivo `.github/workflows/pages.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v4

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

> **Nota:** Como el sitio es HTML puro, no hay paso de build. El contenido se publica directamente desde la raíz del repositorio.

---

## 5. Flujo de trabajo diario

```
Editás un archivo  →  git commit + push  →  GitHub Actions corre  →  Sitio actualizado
      (local)                                    (~60 segundos)
```

Podés editar directamente desde GitHub.com si no tenés acceso a tu computadora.

---

## 6. URL del sitio

Una vez configurado, la URL del sitio será:

```
https://<tu-usuario>.github.io/<nombre-del-repo>/
```

Por ejemplo, si tu usuario es `aleja-vazquez` y el repo es `doc-web`:

```
https://aleja-vazquez.github.io/doc-web/
```

Podés encontrar la URL exacta en **Settings → Pages** después del primer deploy exitoso.

---

## 7. Control de accesos

| Tipo de repo | Visibilidad del sitio | Recomendación |
|---|---|---|
| **Público** | Cualquier persona con el link | Ideal para este curso |
| **Privado** | Solo con GitHub Pro/Team | Para uso interno de empresa |

Para este curso se recomienda mantener el repositorio **público** para que los estudiantes puedan acceder desde cualquier dispositivo sin autenticación.

---

## 8. Agregar contenido nuevo

Para agregar una nueva página al sitio:

1. Crear el archivo `nueva-pagina.html` en la raíz (usando los archivos existentes como plantilla)
2. Agregar el link en la navegación de todos los archivos HTML existentes
3. Hacer commit y push → el sitio se actualiza solo

---

## 9. Verificar el estado del deploy

1. Ir al repositorio → pestaña **Actions**
2. Ver el workflow **Deploy to GitHub Pages**
3. Si el ícono es verde ✅: el sitio está actualizado
4. Si es rojo ❌: revisar los logs del workflow para encontrar el error

---

## Referencias

- [Documentación oficial de GitHub Pages](https://docs.github.com/pages)
- [GitHub Actions para Pages](https://github.com/actions/deploy-pages)
- [Guía de Markdown en GitHub](https://docs.github.com/en/get-started/writing-on-github)
