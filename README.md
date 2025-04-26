[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19144207&assignment_repo_type=AssignmentRepo)
# Lab03: Visualización de Datos en Raspberry Pi Zero W

## Integrantes
[Laura Hernandez Rodriguez](https://github.com/laurafer9810)

[Sergio Ricardo León](https://github.com/SergioRicardo07)

## Documentación
Este laboratorio se hizo con el fin de leer la temperatura interna de nuestra  raspberry, guardar los datos en un archivo csv y realizar la graficas de estas por medio de python.
Se realizo la programacion en python del siguiente código:[monitor temperatura](https://github.com/ECCI-Sistemas-Digitales-3/lab03-g6/blob/main/monitorTemp_funcional) 

## Preguntas

# Respuestas a las Preguntas sobre el Código

1. **¿Qué función cumple `plt.fignum_exists(self.fig.number)` en el ciclo principal?**
   - `plt.fignum_exists(self.fig.number)` verifica si la figura asociada a `self.fig` sigue existiendo. Esto es útil para determinar si el usuario ha cerrado la ventana de la gráfica. Si la figura ya no existe, el ciclo se detiene y el monitoreo finaliza.

2. **¿Por qué se usa `time.sleep(self.intervalo)` y qué pasa si se quita?**
   - `time.sleep(self.intervalo)` se utiliza para pausar la ejecución del programa durante un intervalo específico (0.5 segundos) entre cada actualización de datos y graficado. Si se quita, el ciclo se ejecutaría de manera continua y rápida, lo que podría causar un uso excesivo de la CPU y hacer que la gráfica se actualice demasiado rápido para ser útil.

3. **¿Qué ventaja tiene usar `__init__` para inicializar listas y variables?**
   - Usar `__init__` para inicializar listas y variables permite establecer un estado inicial para los atributos de la clase. Esto asegura que cada instancia de la clase tenga sus propias copias de las listas y variables, evitando conflictos entre instancias y permitiendo un manejo más organizado de los datos.

4. **¿Qué se está midiendo con `self.inicio = time.time()`?**
   - `self.inicio = time.time()` almacena el tiempo actual en segundos. Esto se utiliza como punto de referencia para calcular el tiempo transcurrido desde que comenzó el monitoreo de temperatura.

5. **¿Qué hace exactamente `subprocess.check_output(...)`?**
   - `subprocess.check_output(...)` ejecuta un comando del sistema (en este caso, `vcgencmd measure_temp`) y captura su salida. Devuelve la salida del comando como un objeto de bytes, que luego se decodifica a una cadena de texto para extraer la temperatura.

6. **¿Por qué se almacena `ahora = time.time() - self.inicio` en lugar del tiempo absoluto?**
   - Se almacena `ahora = time.time() - self.inicio` para obtener el tiempo transcurrido desde que comenzó el monitoreo. Esto permite que los datos de tiempo sean relativos al inicio del monitoreo, lo que es más útil para graficar el tiempo transcurrido en lugar de un tiempo absoluto.

7. **¿Por qué se usa `self.ax.clear()` antes de graficar?**
   - `self.ax.clear()` se utiliza para limpiar el área de la gráfica antes de dibujar la nueva serie de datos. Esto evita que las gráficas anteriores se superpongan y asegura que solo se muestre la información más reciente.

8. **¿Qué captura el bloque `try...except` dentro de `leer_temperatura()`?**
   - El bloque `try...except` captura cualquier excepción que pueda ocurrir al intentar leer la temperatura, como problemas al ejecutar el comando o errores de conversión de datos. Si ocurre un error, se imprime un mensaje y se devuelve `None`.

9. **¿Cómo podría modificar el script para guardar las temperaturas en un archivo .csv?**
   - El script ya incluye una función `guardar_datos_csv` que se encarga de guardar las temperaturas en un archivo .csv. Para asegurarte de que se guarden las temperaturas, simplemente asegúrate de que la función `guardar_datos_csv` se llame con los parámetros correctos (que ya se hace en `actualizar_datos`). 
