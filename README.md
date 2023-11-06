## Laboratorio No. 4 - Cinemática Directa - Phantom X - ROS

### Integrantes: 
- Victor Manuel Dávila Castañeda.
- Manuel Felipe Carranza Montenegro.
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
La interfaz gráfica se ha desarrollado utilizando la herramienta App Designer de MATLAB, donde se utilizaron los distintos codigos disponibles en el Dynamixel SDK, se incluye el codigo en el repositorio y aca se explican las partes mas importantes
Con los comandos

```matlab
openport(port_num);
setBaudRate(port_num, BAUDRATE);
```
Se define el purto que en este caso es el "COM5" y se define el baud rate que gracias al dynamixel wizard sabemos que es 1000000
Con la instruccion
```matlab
write1ByteTxRx(port_num, PROTOCOL_VERSION, DXL1_ID, ADDR_MX_TORQUE_ENABLE, TORQUE_ENABLE);
```
Podemos escribir un byte del motor dynamixel que requiere como argumentos el puerto, el la version del protocolo a usar, la id del motor, que es especialmente util cuando se tienen varios motores com es este caso la direccion del byte que se quiere modificar, en este caso es el control de torque, y por ultimo el valor que se le quiere asignar, en este caso seria 1 porque queremos bloquear la posicion de los motores.

Con el siguiente grupo de comandos
```matlab
dxl_addparam_result = groupSyncWriteAddParam(group_num, DXL1_ID, dxl_goal_position(index), LEN_MX_GOAL_POSITION);
dxl_addparam_result = groupSyncWriteAddParam(group_num, DXL2_ID, dxl_goal_position(index), LEN_MX_GOAL_POSITION);
groupSyncWriteTxPacket(group_num);
groupSyncWriteClearParam(group_num);
```
Podemos unir distintas instucciones para modificar los bits de goal position de cada motor, con la funcion  groupSyncWriteAddParam() y con la funcion groupSyncWriteTxPacket(), enviamos todas las instucciones al mismo tiempo logrando que todos los motores vayan a la posicion deseada de manera sincronizada.
La ultima instruccion a destacar que se uso en este programa fu la siguiente
```matlab
dxl1_present_position = read2ByteTxRx(port_num, PROTOCOL_VERSION, DXL1_ID, ADDR_MX_PRESENT_POSITION);
```
Con esta función se puede leer un byte del dynamixel y necesita como argumentos el puerto, la version del protocolo, la id del motor y la direccion del byte que se quiere leer que en este caso es la posicion actual del motor.
Luego de entender como funcionan todas estas funciones, al momento de diseñar la interfaz grafica con el app designer de matlab solo fue necesario arrastrar los elementos que ibamos a utilizar y despues agragar las funciones de event listener para los botones y dentro de ellas escribir los comandos que queriamos que se ejecutaran, la grafica de la posicion actual del robot se ve en una ventana aparte debido a que la funcion de plot del toolbox no permitia integracion con los UIAxes de la GUI de matlab.
Y el resultado obtenido es el siguiente:

<div>
<p style = 'text-align:center;' align="center">
<img width="1438" alt="Screenshot 2023-11-05 at 17 56 14" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/3980c8b8-a016-44b3-8f83-8f129df38e22">
</p>
</div>

## Funcionalidades de la Interfaz Gráfica.

<div>
<p style = 'text-align:center;' align="center">
<img width="872" alt="Screenshot 2023-11-05 at 19 20 47" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/5cd4600c-3be1-428a-8c0d-8d7360ff845a">
</p>
</div>

1) Selección Múltiple de Posiciones Posibles:
Esta opción de selección múltiple permite al usuario visualizar y elegir entre todas las posibles configuraciones cinemáticas que se han establecido para el robot. Esto es especialmente útil para explorar y comparar diferentes posiciones y orientaciones del robot, lo que facilita la interacción con el sistema y la elección de la configuración deseada.

2) Ir a la Posición:
Una vez que se ha seleccionado una configuración cinemática específica, al presionar este botón se envía una señal que efectúa el posicionamiento del robot. Esto significa que el robot se moverá y se ajustará automáticamente a la posición y orientación seleccionada, llevando a cabo la acción deseada. Este botón actúa como un disparador para iniciar el proceso de posicionamiento del robot.

3) Valores para cada Articulación:
Una vez que se ha seleccionado una configuración cinemática específica, al presionar este botón se envía una señal que efectúa el posicionamiento del robot. Esto significa que el robot se moverá y se ajustará automáticamente a la posición y orientación seleccionada, llevando a cabo la acción deseada. Este botón actúa como un disparador para iniciar el proceso de posicionamiento del robot.

4) Última Posición Enviada:
Este botón tiene la función de mostrar de forma gráfica, utilizando el toolbox de Peter Corke, la configuración cinemática del robot que ha sido previamente seleccionada por el usuario en la opción de selección múltiple al inicio. Esta representación gráfica proporciona una visualización visual de la configuración cinemática del robot, lo que permite al usuario tener una comprensión más clara y detallada de la disposición de las articulaciones y los eslabones en la configuración elegida.

5) Posición Actual:
Este botón tiene la función de desactivar el torque en todas las articulaciones del robot. Al hacerlo, el usuario puede modificar manualmente la configuración cinemática del robot. Esta característica permite a los usuarios ajustar la posición y orientación de las articulaciones de forma manual, lo que puede ser útil para tareas de programación o enseñanza. También les permite visualizar la configuración angular de las articulaciones mientras realizan ajustes manuales.

## Comparación Gráficas Digitales vs Gráficas Reales.

Una vez que se ha configurado la interfaz gráfica, se procede a verificar su funcionamiento. Esto implica comparar la pose real del robot con la pose digital generada por la biblioteca de Peter Corke. Al realizar esta comparación y observar que ambas poses son idénticas, se confirma que la interfaz está funcionando correctamente. Esto indica que la representación digital del robot refleja de manera precisa su posición y orientación en el mundo real, lo que es un indicativo de un funcionamiento adecuado de la interfaz, tal como se muestra a continuación para cada una de las poses solicitadas.

#### Pose No. 1 [q1 q2 q3 q4] = [0 0 0 0]

<div>
<p style = 'text-align:center;' align="center">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 09 09" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/b78d42fc-6d35-41f4-a0b7-870f282ae025">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 09 34" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/40e4cff6-0894-4252-bf2e-a7dd80a303ec">
</p>
</div>

#### Pose No. 2 [q1 q2 q3 q4] = [25 25 20 -20]

<div>
<p style = 'text-align:center;' align="center">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 17 07" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/c4db9173-15fa-42d6-a4dd-865aefaece66">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 17 45" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/ec0d87eb-1c09-4435-9e79-cb50ff66ee42">
</p>
</div>

#### Pose No. 3 [q1 q2 q3 q4] = [-35 35 -30 30]

<div>
<p style = 'text-align:center;' align="center">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 19 59" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/ee75f11e-c828-40de-8ca1-af02d9053285">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 20 48" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/192297f9-c7c2-4713-8d3d-cf5415a5c1c7">
</p>
</div>

#### Pose No. 4 [q1 q2 q3 q4] = [85 -20 55 25]

<div>
<p style = 'text-align:center;' align="center">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 25 53" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/6bf25b7f-b3c4-4d70-9e44-c44a44f27d8f">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 26 17" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/76582039-ed23-4270-a8ad-d1201ca73115">
</p>
</div>

#### Pose No. 5 [q1 q2 q3 q4] = [80 -35 55 -45]

<div>
<p style = 'text-align:center;' align="center">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 28 43" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/7e09b735-5d6f-422c-a9fa-3fd6fdad18fd">
<img width="400" height="400" alt="Screenshot 2023-11-05 at 17 29 01" src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/assets/82252851/51a24f88-c1c2-4734-a3ad-f00fa49ec082">
</p>
</div>

## Video del Funcionamiento de la Interfaz Gráfica.

(dar click en la imagne para ir al video)

<div>
<p style = 'text-align:center;' align="center">
<a href="https://www.youtube.com/watch?v=jWy_6WWa2CI" target="_blank"><img src="https://github.com/victordavila2311/LAB4Robotica_Manuel_Victor/blob/main/imagenes%20lab%204/pos%205.png" 
alt="IMAGE ALT TEXT HERE" width="700" height="350" border="10" /></a>
</p>
</div>


