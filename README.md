# VTerm — Landing Page

Página de presentación y descarga de [VTerm](https://github.com/BernabeSuarez/VTerm), una terminal multiplataforma (macOS, Windows, Linux) construida con Electron, React y xterm.js.

Sitio estático de un solo archivo, pensado para desplegarse con **GitHub Pages**.

## Estructura

```
.
└── index.html   # página completa (HTML + CSS + JS inline, sin dependencias locales)
```

No hay build step: es HTML plano. La única dependencia externa es la carga de las fuentes **JetBrains Mono** e **Inter** desde Google Fonts.

## Desarrollo local

Como es un solo archivo estático, alcanza con abrirlo en el navegador:

```bash
open index.html        # macOS
# o servilo con cualquier servidor estático
npx serve .
```

## Publicar en GitHub Pages

1. Asegurate de que `index.html` esté en la raíz del repo (o en `/docs`, según cómo configures Pages).
2. En el repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**.
3. Elegí la branch (`main`) y la carpeta (`/root` o `/docs`).
4. Guardá. GitHub publica el sitio en `https://<usuario>.github.io/<repo>/` (o en un dominio propio si configurás `CNAME`).

Los cambios a `index.html` en la branch configurada se reflejan automáticamente en cada push (puede tardar uno o dos minutos).

## Actualizar los links de descarga

Los tres botones de descarga (macOS / Windows / Linux) apuntan a:

```
https://github.com/BernabeSuarez/VTerm/releases/latest
```

Para que funcionen, VTerm necesita tener al menos una release publicada con los instaladores adjuntos (`.dmg`, `.exe`, AppImage/`.deb`), generados con:

```bash
npm run build:mac    # o build:win / build:linux
```

Si preferís enlazar cada botón a un instalador específico en vez de "latest", reemplazá el `href` de cada `<a class="btn btn-primary">` en `index.html` por la URL directa del asset dentro de la release.

## Personalización

- **Temas mostrados en la sección "Temas"**: son ilustrativos. Para que coincidan con los temas reales de la app, actualizá los valores hexadecimales en los `.theme-card` de `index.html` usando los colores definidos en `src/renderer/src/themes/index.ts` del repo de VTerm.
- **Paleta y tipografía**: definidas como variables CSS al inicio del archivo (`:root`), fáciles de ajustar sin tocar el resto del código.

## Licencia

Misma licencia que el proyecto [VTerm](https://github.com/BernabeSuarez/VTerm).
