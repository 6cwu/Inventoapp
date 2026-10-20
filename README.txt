# Mi Inventario — proyecto para generar APK

Este proyecto empaqueta la aplicación HTML local como una aplicación Android mediante Capacitor.

## Requisitos
- Computadora Windows, macOS o Linux.
- Node.js 22 o superior.
- Android Studio instalado, con Android SDK configurado.

## Pasos (Windows)
1. Extrae esta carpeta ZIP en una ubicación sencilla, por ejemplo `C:\MiInventario`.
2. Abre la carpeta extraída.
3. En el Explorador de archivos, haz clic en la barra de dirección, escribe `cmd` y pulsa Enter.
4. Ejecuta estos comandos, uno por uno:

```bash
npm install
npm install @capacitor/android
npx cap add android
npx cap sync android
npx cap open android
```

5. Android Studio se abrirá. Espera a que termine la sincronización de Gradle.
6. Para compilar una APK instalable de prueba, usa el menú **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
7. Android Studio mostrará un aviso con un enlace para localizar el archivo APK. Normalmente queda en `android/app/build/outputs/apk/debug/`.

## Actualizar la app más adelante
Reemplaza `www/index.html` por la nueva versión del HTML y ejecuta:

```bash
npx cap sync android
```

Después vuelve a generar la APK desde Android Studio.

## Importante
- Los datos del inventario se guardan localmente en el almacenamiento del WebView de la app.
- Desinstalar la aplicación o borrar sus datos puede eliminar el inventario. Usa Exportar CSV o Crear copia JSON dentro de la app para respaldarlo.
- Esta es una APK de prueba/debug. Para distribución pública se recomienda generar una versión firmada de lanzamiento y conservar la clave de firma.


## Compilar sin computadora usando GitHub Actions
Este ZIP también incluye `.github/workflows/build-apk.yml`, un flujo de compilación que puedes ejecutar desde el sitio web de GitHub.

1. Crea un repositorio en GitHub. Si eliges público, cualquiera podrá ver el código.
2. Sube todos los archivos y carpetas de este ZIP al repositorio, incluyendo la carpeta oculta `.github/workflows/`.
3. En la página del repositorio, abre la pestaña **Actions**.
4. Selecciona **Compilar APK de Mi Inventario** y pulsa **Run workflow**.
5. Espera a que termine la ejecución. Abre la ejecución completada y descarga el artefacto **Mi-Inventario-APK**.
6. Extrae el ZIP del artefacto y abre `app-debug.apk` en tu Android para instalarla. Android puede pedir autorización para instalar desde esa fuente.

Si no aparece el flujo en Actions, confirma que `.github/workflows/build-apk.yml` se subió con esa ruta exacta. La primera compilación puede fallar si cambia alguna dependencia; revisa el registro de ejecución.
