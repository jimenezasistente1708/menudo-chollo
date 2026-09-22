# Menudo Chollo: cómo se actualiza y se publica

## Estructura
- `index.html`, `css/styles.css`, `js/app.js`: la web. No se tocan a diario.
- `data/productos.json`: TODO lo que cambia (ajustes, tiendas, categorías y productos).
- `herramientas/`: scripts opcionales y gratuitos (Python 3).
- `aviso-legal.html`, `privacidad.html`, `cookies.html`, `afiliacion.html`: completa los campos [COMPLETAR].
- `_headers`, `robots.txt`: ajustes para Cloudflare Pages.

## Antes de publicar (una sola vez)
1. En `data/productos.json`: `"modoDemo": false`, `"whatsappUrl": "<enlace de tu canal>"`.
2. Completa los campos [COMPLETAR] de las páginas legales.
3. Borra los productos de ejemplo y añade los reales.
4. `python3 herramientas/validar.py` debe terminar sin errores.

## Añadir chollos (día a día)
Opción A: edita `productos.json` copiando un bloque de producto.
Opción B (sin tocar código): rellena `herramientas/productos.csv` en Excel o Google Sheets,
guárdalo como "CSV UTF-8" y ejecuta:
    python3 herramientas/csv_a_json.py
    python3 herramientas/validar.py

Reglas de los datos:
- Amazon: pega el enlace normal del producto; la web añade tu tag. No mostrará precio ni imagen de Amazon (política de Amazon).
- AliExpress y eBay: pega en `url` el enlace de afiliado que genera tu panel. La web no lo modifica.
- Pon `actualizado` con la fecha en que comprobaste el precio (AAAA-MM-DD). Pasados `caducidadDias` (7 por defecto) el chollo desaparece solo.
- `precio` y `precioAnterior`: solo precios reales que hayas comprobado.
- `envio`: gratis, pago o desconocido.

## Probar en tu ordenador
La web carga un archivo JSON, así que no funciona abriendo index.html con doble clic. Usa:
    python3 -m http.server 8000
y abre http://localhost:8000

## Publicar en Cloudflare Pages (gratis)
Opción 1: sube esta carpeta a un repositorio de GitHub y conéctalo a Cloudflare Pages
(sin comando de compilación; carpeta de salida: la raíz). Cada cambio que subas se publica solo.
Opción 2: subida directa de la carpeta desde el panel de Cloudflare Pages.
