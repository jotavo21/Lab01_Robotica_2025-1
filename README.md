# Laboratorio 01 Robótica - Trayectorias, Entradas y Salidas Digitales
En este laboratorio se estudiaron las funciones básicas del robot industrial ABB IRB 140 y su programación usando el software RobotStudio, para esto se diseño una herramienta adecuada para el manipulador capaz de sostener un marcador y se programó una rutina que permitiera al robot escribir el primer nombre de ambos integrantes del grupo, además de un símbolo en un objeto de trabajo escogido para la práctica.
## Descripción detallada de la solución planteada

## Diagrama de flujo de acciones del robot
## Plano de planta de la ubicación de cada uno de los elementos
## Descripción de las funciones utilizadas
Para el funcionamiento del robot se usaron las siguientes funciones:  
+Path_I, Path_IA, Path_IAN: Estas funcionas se encargan de realizar el trazado de las letras del primer nombre, usando MoveJ para la aproximación al target 1.  
+Path_J, Path_JU, Path_JUA, Path_JUAN: Estas funcionas se encargan de realizar el trazado de las letras del segundo nombre, usando MoveJ para la aproximación al target 1.  
+Path_Intermedio: Esta función lleva la herramienta a un target posicionado arriba de la caja.  
+Path_Superior: Está funcion permite que el robot pase al lado de la banda sin golpear objetos en la trayectoria hasta la caja.  
+Path_Mantenimiento: Esta función lleva al robot a una posición dónde se le pueda cambiar la herramienta de manera sencilla.  
+Path_Off:
+Path_Home:
## Diseño de la herramienta detallado 
## Video que contenga la simulación en RobotStudio así como la implementación de la práctica con los robots reales
