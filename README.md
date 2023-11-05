## Laboratorio No. 4 - Cinemática Directa - Phantom X - ROS

### Integrantes: 
- Victor Manuel Dávila Castañeda.
- Manuel Felipe Carranza Montenegro.
- 
## Descripción de la Solución Planteada.

### Robot Phantom X Pincher.

<div>
<p style = 'text-align:center;' align="center">
<img width="331" alt="Screenshot 2023-11-05 at 16 09 48" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/c9cee074-3028-41f7-be09-69e8486836a0">
</p>
</div>

## Análisis de Articulaciones y Eslabones.
En una primera fase, se inicia con el análisis de las articulaciones y eslabones del robot Phantom X Pincher. Este paso es fundamental para identificar los factores esenciales requeridos con el fin de llevar a cabo la cinemática directa del robot. Además, este análisis es crucial para la generación de la tabla que contendrá los parámetros de la convención Denavit-Hartenberg estándar (DHstd):

<div>
<p style = 'text-align:center;' align="center">
<img width="324" height="500" alt="Screenshot 2023-11-05 at 16 10 26" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/0e6d9e56-c8ee-4e8a-82c4-c56a02acc563">
<img width="324" height="500" alt="Screenshot 2023-11-05 at 16 10 56" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/56b82910-20cb-4a42-9903-d4ff5b23c540">
</p>
</div>
  
## Tabla de Parámetros de Denavit-Hartenberg Estándar (DHstd).
Una vez completado el análisis de los eslabones y articulaciones, se procede a la creación de la tabla de parámetros. Esta tabla contendrá información esencial que permitirá describir de manera precisa la configuración cinemática del robot.

<div>
<p style = 'text-align:center;' align="center">
<img width="415" alt="Screenshot 2023-11-05 at 16 11 22" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/fc2caf84-8354-4d69-9f73-4d5c8e837d34">
</p>
</div>

## Comprobación Cinemática Directa.
Una vez que se han determinado los parámetros, se procede a realizar la verificación utilizando la biblioteca de Peter Corke. Esta etapa es esencial para asegurarse de que los cálculos de cinemática directa del robot sean precisos y confiables.

<div>
<p style = 'text-align:center;' align="center">
<img width="522" alt="Screenshot 2023-11-05 at 16 20 15" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/1910032c-6564-494e-8f48-10b358faa4d0">
</p>
</div>

#### Se definen los Parámetros del Robot: 
En este paso, se establecen las longitudes de los eslabones del robot, que representan las distancias entre las articulaciones. Estos valores se asignan a las variables l_1, l_2, l_3 y l_4.

#### Creación de Objetos de Enlace: 
Se crean objetos de enlace para cada articulación del robot. Cada enlace se define con sus propias características, como el tipo de articulación (en este caso, revoluta), los límites de movimiento (qlim), las distancias "d" y los ángulos "a" y "alpha". Estos objetos de enlace se almacenan en un vector L.

#### Creación del Objeto de Robot Serial: 
Se crea un objeto de robot serial llamado "ROBOT" utilizando los objetos de enlace definidos anteriormente. Este objeto representa el robot completo y se utiliza para realizar cálculos y simulaciones posteriores.

#### Definición de la Herramienta del Robot: 
Se define la herramienta (Tool) del robot, que es una transformación rígida que se aplica en la punta del brazo robótico. En este caso, se establece la herramienta como una rotación trotx(0) y una translación transl(0, 0, 0), lo que significa que la herramienta se encuentra en la posición y orientación inicial del extremo del robot.

#### Visualización del Robot: 
Se utiliza la función "ROBOT.plot" para visualizar el robot en una configuración inicial. Se proporciona una secuencia de valores de articulación [0 pi/2 0 0] que define la posición y orientación inicial del robot. Además, se establecen límites de visualización para los ejes X, Y y Z, y se ajusta la vista de la representación gráfica del robot.

## Visualización del Robot en Posición de Home.

<div>
<p style = 'text-align:center;' align="center">
<img width="453" alt="Screenshot 2023-11-05 at 16 33 01" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/ff084d47-4caa-47d8-beb3-70885cd4330a">
</p>
</div>

## Matríz de Transformación Homogénea (MTH).
Ahora, se procede al cálculo de las matrices de transformación homogénea (MTH) para cada eslabón del robot. Posteriormente, se calcula la matriz de transformación homogénea total que representa el robot en su conjunto. Estas matrices de transformación homogénea son esenciales en la cinemática directa de un robot, ya que se utilizan para relacionar las posiciones y orientaciones de las articulaciones con la posición y orientación del extremo del robot. Son herramientas cruciales para determinar la posición y orientación del robot en el espacio tridimensional.

<div>
<p style = 'text-align:center;' align="center">
<img width="420" alt="Screenshot 2023-11-05 at 16 39 16" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/7913c33c-66ab-44e4-ab4d-0fece8088dde">
</p>
</div>

## Diseño Interfaz Gráfica.


## Comparación Gráficas Digitales vs Gráficas Reales.

#### Pose [q1 q2 q3 q4] = [0 0 0 0]

<div>
<p style = 'text-align:center;' align="center">
<img width="450" height="450" alt="Screenshot 2023-11-05 at 17 09 09" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/b78d42fc-6d35-41f4-a0b7-870f282ae025">
<img width="450" height="450" alt="Screenshot 2023-11-05 at 17 09 34" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/40e4cff6-0894-4252-bf2e-a7dd80a303ec">
</p>
</div>

#### Pose [q1 q2 q3 q4] = [25 25 20 -20]

<div>
<p style = 'text-align:center;' align="center">
<img width="450" height="450" alt="Screenshot 2023-11-05 at 17 17 07" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/c4db9173-15fa-42d6-a4dd-865aefaece66">
<img width="450" height="450" alt="Screenshot 2023-11-05 at 17 17 45" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/ec0d87eb-1c09-4435-9e79-cb50ff66ee42">
</p>
</div>

#### Pose [q1 q2 q3 q4] = [-35 35 -30 30]

<div>
<p style = 'text-align:center;' align="center">
<img width="450" height="450" alt="Screenshot 2023-11-05 at 17 19 59" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/ee75f11e-c828-40de-8ca1-af02d9053285">
<img width="450" height="450" alt="Screenshot 2023-11-05 at 17 20 48" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/192297f9-c7c2-4713-8d3d-cf5415a5c1c7">
</p>
</div>



















