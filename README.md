# LLUVIA POS - Proyecto Android

App nativa Android (WebView) que empaqueta tu sistema de punto de venta
"Lluvia de Hamburguesas" para funcionar sin internet, con ícono propio
(tu logo) y nombre **LLUVIA POS**.

## Opción 1: compilar con GitHub Actions (recomendado, sin instalar nada)

1. Crea un repositorio nuevo en GitHub (puede ser privado).
2. Sube TODO el contenido de esta carpeta tal cual (respetando la
   estructura de carpetas) a la raíz del repositorio.
3. Entra a la pestaña **Actions** del repositorio. Si no se disparó
   solo, dale a **"Build APK" → Run workflow**.
4. Espera a que termine (unos 3-5 minutos). Al terminar, entra al run
   y descarga el archivo **LLUVIA-POS-debug-apk** en la sección
   "Artifacts" — ahí está tu `app-debug.apk`.
5. Pasa ese `.apk` a tu tablet (por USB, WhatsApp, Drive, etc.),
   ábrelo y acepta instalar "de fuentes desconocidas" cuando te lo
   pida Android.

Este primer build genera un APK de **debug**, que se instala y
funciona perfecto para uso propio. Si más adelante quieres subirlo a
la Play Store, se necesita además firmarlo como "release" (te puedo
ayudar con eso cuando lo necesites).

## Opción 2: compilar en tu computadora con Android Studio

1. Instala [Android Studio](https://developer.android.com/studio).
2. Abre esta carpeta como proyecto ("Open an existing project").
3. Deja que termine de sincronizar (descargará lo que le falte, pide
   internet la primera vez).
4. Menú **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
5. El APK queda en `app/build/outputs/apk/debug/app-debug.apk`.

## Qué contiene el proyecto

- `app/src/main/assets/www/index.html` — tu POS completo (Caja,
  Productos, Ventas, Administración), igual al que ya usabas en el
  navegador, pero conectado al sistema Android para poder:
  - Elegir fotos de productos desde la galería.
  - Guardar los CSV del corte del día y el respaldo directamente en
    la carpeta **Descargas/LluviaPOS** de la tablet.
- `app/src/main/java/.../MainActivity.java` — la app nativa: solo
  muestra ese HTML en pantalla completa, en horizontal.
- Ícono de la app en todas las resoluciones (`mipmap-*`), generado a
  partir de tu logo.
- `.github/workflows/build.yml` — automatiza la compilación en
  GitHub.

## Datos de la app

- Todo (productos, ventas, caja) se guarda dentro de la app misma en
  la tablet — no se borra al cerrarla, solo si desinstalas la app o
  borras sus datos desde Ajustes.
- Usa el botón **"Exportar respaldo"** de vez en cuando (queda en
  Descargas/LluviaPOS) por si necesitas restaurarlo en otra tablet.
