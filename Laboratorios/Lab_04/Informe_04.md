# LABORATORIO 4: USO DE BITALINO PARA ECG

## Índice

1. [Objetivos](#objetivos)
2. [Materiales y equipos](#materiales-y-equipos)
3. [Resultados](#resultados)
   - 3.1 [Conexión usada](#conexión-usada)
   - 3.2 [Video de la señal](#video-de-la-señal)
   - 3.3 [Ploteo de la señal en OpenSignal](#ploteo-de-la-señal-en-opensignal)
   - 3.4 [Archivos](#archivos)
   - 3.5 [Ploteo de la señal en Python](#ploteo-de-la-señal-en-python)
4. [Preguntas de la sesion](#preguntas-de-la-sesion)

## Objetivos

- Adquirir señales electrocardiográficas (ECG) en tiempo real utilizando BITalino y OpenSignals.
- Probar diferentes posiciones de los electrodos para las derivaciones I, II y III de Einthoven.
- Comparar cómo cambia la señal ECG según la derivación y la ubicación de los electrodos.
- Relacionar las partes principales de la señal ECG con la actividad eléctrica del corazón.

Se realizaron adquisiciones en:

- 
- 

## Materiales y equipos
- BITalino (r)evolution Core BT.
- Sensor de electrocardiografía (ECG).
- Tres electrodos desechables autoadhesivos de Ag/AgCl con gel.
- OpenSignals (r)evolution.
- Adaptador Bluetooth.

## Procedimiento general
El sensor ECG se conectó a uno de los canales analógicos disponibles del BITalino. Después, los tres cables del sensor se conectaron a sus respectivos electrodos: entrada positiva (IN+), entrada negativa (IN-) y referencia (REF). Una vez revisada la conexión, se inició el registro en OpenSignals.

En cada adquisición se siguió esta secuencia:
- Se registró una línea basal durante 30 segundos, manteniendo una respiración normal y evitando movimientos.
- Se repitió tres veces el ciclo de inhalación, apnea, exhalación y apnea. Cada etapa duró cinco segundos.
- Se registró una nueva línea basal durante 30 segundos.
- Se realizaron 10 burpees para observar la frecuencia cardiaca antes, durante y después del ejercicio.
- Se registró otra línea basal durante 30 segundos.
- Se realizó una inhalación prolongada de aproximadamente 10 segundos y luego se mantuvo la respiración durante aproximadamente 10 segundos.
- Finalmente, se detuvo la adquisición y se guardaron los datos.

## Resultados

## PRUEBA 1: Derivación I

### Conexión utilizada (NO ESTOY SEGURO)
En esta prueba se utilizó la derivación I de Einthoven. El electrodo positivo, conectado al cable rojo (IN+), se colocó sobre la clavícula izquierda. El electrodo negativo, conectado al cable negro (IN-), se ubicó sobre la clavícula derecha. El electrodo de referencia, conectado al cable blanco (REF), se colocó en la cresta ilíaca. 

<p align="center">
  <img src="./Imágenes/prueba1_conexión.jpg" alt="Conexión de prueba" width="500">
</p>

#### A. Línea basal inicial
El participante permaneció en reposo durante 30 segundos, respirando normalmente y evitando movimientos. Esta parte permitió registrar una señal basal con el menor ruido posible.

https://github.com/user-attachments/assets/7d7d8282-91c8-47d0-ba61-9d6debcc7626


#### B. Ciclo respiratorio
Se realizaron tres ciclos de inhalación, apnea, exhalación y apnea. Cada una de estas etapas se mantuvo durante cinco segundos. El objetivo fue observar si la respiración producía variaciones en la señal ECG.



#### C. Actividad física
Después de registrar una segunda línea basal de 30 segundos, el participante realizó 10 burpees. Se mantuvo la adquisición antes, durante y después del ejercicio para observar los cambios de la frecuencia cardiaca.

https://github.com/user-attachments/assets/5fe2c770-742a-4797-83d4-41a29cac6695

#### D. Inhalación prolongada y apnea
Luego de una tercera línea basal de 30 segundos, el participante realizó una inhalación prolongada de aproximadamente 10 segundos y mantuvo la respiración durante aproximadamente 10 segundos.

https://github.com/user-attachments/assets/c32edcd3-f383-4ba3-9b65-f405412b2bfe



### Video de la señal 


#### A. Línea basal inicial


#### B. Ciclo respiratorio


#### C. Actividad física


#### D. Inhalación prolongada y apnea


### Ploteo de la señal en OpenSignal 


### Archivos
Archivos

### Ploteo de la señal en Python
Ploteo de la señal en Python



## PRUEBA 2: Derivación II

### Conexión utilizada (NO ESTOY SEGURO)
En esta prueba se utilizó la derivación II de Einthoven, la cual registra la señal desde el brazo derecho, correspondiente al polo negativo, hacia la pierna izquierda, correspondiente al polo positivo.

Para obtener esta configuración a partir de la derivación I, se intercambiaron las posiciones del electrodo positivo rojo (IN+) y del electrodo de referencia blanco (REF), de acuerdo con el esquema presentado en la guía. Se utilizó la ubicación corporal en la que se había obtenido la señal más clara.

<p align="center">
  <img src="./Imágenes/prueba2_conexión.png" alt="Conexión de prueba 2" width="500">
</p>


#### A. Línea basal inicial
El participante permaneció en reposo durante 30 segundos, respirando normalmente y evitando movimientos. Este registro se utilizó como línea basal de la derivación II.

https://github.com/user-attachments/assets/d8814ab4-fb6f-4e16-b76a-a65e575d9085


#### B. Ciclo respiratorio
Se realizaron tres ciclos de inhalación, apnea, exhalación y apnea. Cada etapa se mantuvo durante cinco segundos, mientras el participante evitaba realizar movimientos adicionales.



#### C. Actividad física
Después de una segunda línea basal de 30 segundos, el participante realizó 10 burpees. La señal se registró antes, durante y después del ejercicio.

https://github.com/user-attachments/assets/c2fcb044-5dac-4cd2-b5eb-d6344efd8973

#### D. Inhalación prolongada y apnea
Después de una tercera línea basal, el participante realizó una inhalación prolongada durante aproximadamente 10 segundos y mantuvo la respiración durante otros 10 segundos.

https://github.com/user-attachments/assets/4a5d418c-aa11-4dcd-8c74-164994804043







### Video de la señal 


#### A. Línea basal inicial



#### B. Ciclo respiratorio



#### C. Actividad física



#### D. Inhalación prolongada y apnea






### Ploteo de la señal en OpenSignal 


### Archivos
Archivos

### Ploteo de la señal en Python
Ploteo de la señal en Python




## PRUEBA 3: Derivación III

### Conexión utilizada (NO ESTOY SEGURO)
En esta prueba se utilizó la derivación III de Einthoven, la cual registra la señal desde el brazo izquierdo, correspondiente al polo negativo, hacia la pierna izquierda, correspondiente al polo positivo.

Para cambiar de la derivación II a la derivación III, se intercambiaron las posiciones del electrodo negativo negro (IN−) y del electrodo de referencia blanco (REF), siguiendo el esquema indicado en la guía. Se mantuvo la misma ubicación corporal utilizada para la derivación II.

<p align="center">
  <img src="./Imágenes/prueba3_conexión.jpg" alt="Conexión de prueba 3" width="500">
</p>


#### A. Línea basal inicial
El participante permaneció en reposo durante 30 segundos, respirando normalmente y evitando movimientos. Esta etapa permitió obtener la línea basal de la derivación III.

https://github.com/user-attachments/assets/161a731d-d6a2-48fe-adad-bcf8fa3ecc25

#### B. Ciclo respiratorio
Se realizaron tres ciclos de inhalación, apnea, exhalación y apnea. Cada etapa tuvo una duración de cinco segundos.



#### C. Actividad física
Luego de registrar una segunda línea basal, el participante realizó 10 burpees. La adquisición se mantuvo antes, durante y después del ejercicio para observar los cambios en la frecuencia cardiaca.

 https://github.com/user-attachments/assets/aec6b3a4-caf0-4b57-a255-c6e012211248

#### D. Inhalación prolongada y apnea
Después de una tercera línea basal, el participante realizó una inhalación prolongada durante aproximadamente 10 segundos y mantuvo la respiración durante otros 10 segundos.

https://github.com/user-attachments/assets/869587b5-dbec-4f50-a69a-dcaad1c3abbf



### Video de la señal 


#### A. Línea basal inicial



#### B. Ciclo respiratorio



#### C. Actividad física



#### D. Inhalación prolongada y apnea


### Ploteo de la señal en OpenSignal 


### Archivos
Archivos

### Ploteo de la señal en Python
Ploteo de la señal en Python



## Preguntas de la sesión

   - **¿Cuáles son las fuentes de ruido más comunes que afectan a una señal de ECG?** (will)


   - **¿Por qué el cambio en la posición de los electrodos, entre las derivaciones I, II y III, modifica los componentes de la señal ECG? ¿Cómo cambian estos componentes?** (will)
   

   - **¿Existen diferencias importantes al adquirir la señal ECG en distintas partes del cuerpo, como las muñecas, las clavículas o el pecho? ¿Cuál podría ser la causa? ¿Esperaba observar estos cambios? Muestre un segmento de la señal obtenida en cada ubicación para visualizar las diferencias.**  (will)


   - **Los sistemas cardiaco y respiratorio se encuentran relacionados. ¿Considera que las distintas formas de respiración, como una respiración más rápida o profunda, pueden influir en la señal ECG? Muestre capturas de las señales obtenidas bajo diferentes condiciones respiratorias y describa las variaciones observadas, si las hubiera.** (jairo)


   - **En la Home-Guide n.º 1 se observó que diferentes niveles de fuerza muscular producían señales con amplitudes distintas. ¿Cómo influye el movimiento en la señal ECG?** (jairo)



   - **Según sus conocimientos, ¿cómo se pueden detectar la bradicardia y la taquicardia en una señal ECG?** (jairo)

   


