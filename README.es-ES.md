# espeak-builder

Flujo de trabajo de GitHub Actions para compilar `libespeak-ng.so` para Android con la API pública de C expuesta.

## Qué compila esto

- `libespeak-ng.so` para **arm64-v8a** (teléfonos Android modernos)
- `libespeak-ng.so` para **armeabi-v7a** (teléfonos Android antiguos)
- Carpeta `espeak-ng-data/` (diccionarios, datos de fonemas, voces)

## ¿Por qué?

El APK oficial de espeak-ng para Android vincula estáticamente la librería en un envoltorio JNI, ocultando la API de C pura. Esta compilación crea una librería compartida independiente con símbolos exportados como `espeak_TextToPhonemes` que pueden ser llamados directamente a través de Dart FFI.

## Uso

1. Ve a la pestaña **Actions**
2. Haz clic en la ejecución del flujo de trabajo exitosa más reciente
3. Descarga el artefacto `espeak-android-build`
4. Extrae y usa en tu proyecto de Flutter/Android:
   - Coloca los archivos `.so` en `android/app/src/main/jniLibs/`
   - Coloca `espeak-ng-data` en los assets de tu aplicación

## Desencadenadores de compilación

- Push a la rama main
- Activación manual vía `workflow_dispatch`

## Licencia

espeak-ng está licenciado bajo GPL-3.0. Consulta https://github.com/espeak-ng/espeak-ng
