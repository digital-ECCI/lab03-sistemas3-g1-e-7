[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/xB5owuT7)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23205485&assignment_repo_type=AssignmentRepo)
# Lab03: Visualización interactiva de datos en Raspberry Pi usando Python y Matplotlib

## Integrantes
Jesus Andre Bojaca
Juan Carlos Barragan 
Julian Camilo Montaño
## Documentación

El programa desarrollado permite monitorear en tiempo real la temperatura de la CPU de una Raspberry Pi y representarla gráficamente.

Para ello se utlizan  las siguientes librerías:

matplotlib.pyplot: utilizada para generar y actualizar la gráfica de temperatura.
time: empleada para medir el tiempo transcurrido y controlar el intervalo entre lecturas.
subprocess: permite ejecutar comandos del sistema operativo desde Python.

El script se organiza mediante la clase MonitorTemperaturaRPI, la cual contiene los métodos necesarios para realizar el monitoreo.

__init__(): inicializa las variables, listas y la ventana de la gráfica.
leer_temperatura(): ejecuta el comando vcgencmd measure_temp y obtiene la temperatura actual del procesador.
actualizar_datos(): almacena las lecturas de temperatura y el tiempo correspondiente, eliminando los datos antiguos para conservar solo los últimos 60 segundos.
graficar(): actualiza la gráfica con los datos más recientes.
ejecutar(): mantiene el ciclo principal del programa hasta que el usuario cierre la ventana o interrumpa la ejecución.

El programa utiliza una gráfica dinámica donde:

El eje X representa el tiempo transcurrido en segundos.
El eje Y representa la temperatura de la CPU en grados Celsius.

## Preguntas

1. ¿Qué función cumple ```plt.fignum_exists(self.fig.number)``` en el ciclo principal?
R// : Verifica si la ventana de la gráfica todavía existe. Mientras la ventana siga abierta, el ciclo continúa ejecutándose. Si el usuario la cierra, la función devuelve False y el programa termina

2. ¿Por qué se usa ```time.sleep(self.intervalo)``` y qué pasa si se quita?
R//:hace que el programa espere un tiempo entre una lectura y la siguiente. En este caso espera 0.5 s.

3. ¿Qué ventaja tiene usar ```__init__``` para inicializar listas y variables?
R//Se usa para inicializar atributos cuando se crea el objeto

4. ¿Qué se está midiendo con ```self.inicio = time.time()```?
R//:Guarda el instante exacto en que comenzó el monitoreo.

time.time() devuelve el número de segundos transcurridos desde el 1 de enero de 1970 (tiempo Unix). Ese valor se usa luego como referencia para medir cuánto tiempo ha pasado.

5. ¿Qué hace exactamente ```subprocess.check_output(...)```?
R// ejecuta un comando del sistema operativo y devuelve lo que ese comando imprime.

6. ¿Por qué se almacena ```ahora = time.time() - self.inicio``` en lugar del tiempo absoluto?
R//obtener el tiempo transcurrido desde que empezó el programa
7. ¿Por qué se usa ```self.ax.clear()``` antes de graficar?
R// Este borra la gráfica anterior antes de dibujar la nueva.
8. ¿Qué captura el bloque ```try...except``` dentro de ```leer_temperatura()```?
R//:El bloque try...except dentro de leer_temperatura() captura errores al intentar leer la temperatura.
9. ¿Cómo podría modificar el script para guardar las temperaturas en un archivo .```csv```?
R// Se debe agregar el impor CSV
"with open("temperaturas.csv", "w", newline="") as archivo:
    escritor = csv.writer(archivo)
    escritor.writerow(["Tiempo (s)", "Temperatura (°C)"])"