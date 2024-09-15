# multibranch-sample-app

## Solución a errores de incompatibilidad de archivos `gradlew` en entornos Linux

Si te encuentras con el siguiente error al ejecutar una pipeline en Jenkins o al correr el script `gradlew` en un entorno Linux:

/usr/bin/env: ‘sh\r’: No such file or directory

Este error ocurre debido a que el archivo `gradlew` fue guardado con saltos de línea de Windows (`CRLF`), lo que provoca problemas en sistemas basados en Unix, como Linux, que esperan saltos de línea de tipo `LF`.

### Solución

Para resolver este problema, debes convertir el archivo `gradlew` para que use el formato de salto de línea correcto (`LF`). A continuación, te mostramos cómo hacerlo:

1. **Accede al contenedor o máquina donde se ejecuta el pipeline de Jenkins**.
   
2. **Convierte el archivo `gradlew`** usando el comando `dos2unix` o una alternativa con `sed`:

   Con `dos2unix` (si está disponible):

   ```bash
   dos2unix ./gradlew
