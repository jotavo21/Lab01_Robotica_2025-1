# Laboratorio 01 Robótica - Trayectorias, Entradas y Salidas Digitales
En este laboratorio se estudiaron las funciones básicas del robot industrial ABB IRB 140 y su programación usando el software RobotStudio, para esto se diseño una herramienta adecuada para el manipulador capaz de sostener un marcador y se programó una rutina que permitiera al robot escribir el primer nombre de ambos integrantes del grupo, además de un símbolo en un objeto de trabajo escogido para la práctica. El diseño propuesto para lo que se escribirá se muestra a continuación:
![image](https://github.com/jotavo21/Lab01_Robotica_2025-1/blob/main/imagenes/Trayectoria%20propuesta.png)  

## Descripción detallada de la solución planteada
### Calibración
Primero se calibró la herramienta diseñada para la práctica. Para calibrar la herramienta esta se debe acoplar al manipulador, luego se debe tocar el mismo punto desde cuatro direcciones distintas, es decir, desde diferentes configuraciones del robot. Al finalizar la calibración, se obtuvo un error medio de 2.918mm. A continuación se muestra los resultados obtenidos en la calibración:
![image](https://github.com/jotavo21/Lab01_Robotica_2025-1/blob/main/imagenes/Calib%20manual.jpg)  

Luego, se calibró el workobject. Para calibrar el workobject, se debe tener el objeto sobre el que se va a trabajar y crear un workobject en el software de ABB, finalmente se definen 3 puntos sobre el workobject, el primer punto indica el origen del workobject, el segundo indica el eje en X y el tercero el eje en Y. A continuación se muestran los resultados de la definición y calibración del workobject:
![image](https://github.com/jotavo21/Lab01_Robotica_2025-1/blob/main/imagenes/Workobject.jpg)  

### Creación de las Rutinas  
Para la creación de las rutinas en RobotStudio, el primer paso consiste en exportar el archivo .dwg que contiene las trayectorias previamente diseñadas en AutoCAD. Este archivo define las formas o textos que el robot deberá seguir durante su ejecución.  

Una vez importado el modelo al entorno de trabajo, se procede a crear los targets en los puntos más relevantes de la trayectoria, tales como los puntos iniciales, intermedios y finales. Estos puntos constituyen las referencias espaciales que permiten al robot reproducir con precisión el movimiento deseado.  

Posteriormente, se definen los paths correspondientes a cada trayectoria. En una primera versión, se estableció un path independiente para cada nombre; sin embargo, esto generó problemas de continuidad en la línea, debido a la proximidad entre los segmentos. Para resolverlo, se incorporó un path intermedio de transición, que permite alejar temporalmente la herramienta del objeto, evitando así colisiones o trazos indeseados y mejorando la fluidez general del movimiento.  

En la programación RAPID, los targets iniciales fueron ajustados utilizando la instrucción MoveJ en lugar de MoveL, con el fin de permitir mayores tolerancias en el posicionamiento durante las fases de aproximación. Esta modificación facilita movimientos más suaves y rápidos, especialmente en zonas donde la precisión absoluta no es crítica. Además, se adaptaron las velocidades para aprovechar la máxima capacidad operativa del robot sin comprometer la estabilidad del proceso.  

Finalmente, para prevenir errores durante la ejecución, fue necesario unificar las configuraciones de los targets (orientación, herramienta y objeto de trabajo). Para ello, se empleó la herramienta de “Buscar y Reemplazar” en RAPID, que permite garantizar la coherencia entre los distintos puntos de la trayectoria y evitar inconsistencias de configuración que puedan generar fallas en la simulación o en la ejecución real.  

## Diagrama de flujo de acciones del robot
![image](https://github.com/jotavo21/Lab01_Robotica_2025-1/blob/main/imagenes/Diagrama%20flujo%20robot.png)  

## Plano de planta de la ubicación de cada uno de los elementos
Revisar en el Repositorio los documentos adjuntos.  

## Descripción de las funciones utilizadas
Para el funcionamiento del robot se usaron las siguientes funciones:  
+Path_I, Path_IA, Path_IAN: Estas funcionas se encargan de realizar el trazado de las letras del primer nombre, usando MoveJ para la aproximación al target 1.  
+Path_J, Path_JU, Path_JUA, Path_JUAN: Estas funcionas se encargan de realizar el trazado de las letras del segundo nombre, usando MoveJ para la aproximación al target 1.   
+Path_R1: Esta rutina dibuja una figura de un rostro robótico sin levantar la herramienta. 
+Path_Intermedio: Esta función lleva la herramienta a un target posicionado arriba de la caja.  
+Path_Superior: Está funcion permite que el robot pase al lado de la banda sin golpear objetos en la trayectoria hasta la caja.  
+Path_Mantenimiento: Esta función lleva al robot a una posición dónde se le pueda cambiar la herramienta de manera sencilla.  
+Path_Off: Está rutina lleva al robot a una posición dónde todas sus articulaciones estén en 0 grados.  
+Path_Home:Esta Posición lleva al robot a la posición inicial, dónde el 6to gdl, no esté en 0 para evitar el Lock Gimbal.  
## Diseño de la herramienta detallado 
La herramienta utilizada durante la actividad se diseñó considerando dos aspectos principales. En primer lugar, se revisó la hoja técnica del robot ABB IRB 140 para determinar las dimensiones del flange del manipulador y el tamaño adecuado de la rosca a emplear. Finalmente, se estableció que el ángulo de la herramienta fuera de 60 grados, con el propósito de evitar singularidades del tipo *lock gimbal*, las cuales ocurren cuando dos o más articulaciones del robot se alinean.  

![image](https://github.com/jotavo21/Lab01_Robotica_2025-1/blob/main/imagenes/Screenshot%202025-10-05%20203235.png)
## Video que contenga la simulación en RobotStudio así como la implementación de la práctica con los robots reales
