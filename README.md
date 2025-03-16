# Sistema Satelital   
## 1.	Presentación del proyecto    
### 1.1	Visión global     
El proyecto consiste en la implementación del prototipo de un sistema satelital como el mostrado en la figura. El sistema satelital se compone de dos elementos fundamentales: el satélite y la estación de tierra.    
   
El satélite se encarga de captar datos del espacio, procesarlos y enviarlos periódicamente a la estación de tierra. También recibe órdenes de la estación de tierra que pueden modificar alguna de las tareas que realiza.    
   
La estación de tierra recibe los datos que le envía el satélite y se los muestra al usuario de la manera más clara posible a través de una interfaz gráfica amigable, desde la que el usuario también puede enviar órdenes al satélite.    

<img src="https://github.com/user-attachments/assets/e323d51f-95e6-4069-9fa2-d090085aab35" width="400" height="200">      

### 1.2	 El satélite    
El elemento principal del satélite es un microprocesador Arduino, que llamaremos controlador. El satélite también está equipado con sensores que permiten al controlador adquirir datos de humedad, temperatura y proximidad de objetos que pueden impactar contra el satélite. Además, dispone de sistemas mecánicos que le permiten cambiar la orientación de alguno de los sensores (por ejemplo, del sensor de proximidad).     
   
El controlador también es capaz de proporcionar datos sobre su posición exacta en la órbita que recorre. Y naturalmente, está equipado con los componentes necesarios para comunicarse con la estación de tierra.    
   
El controlador está programado en lenguaje C. El programa obtiene los datos de los diferentes sensores, realiza ciertos procesados de los datos, los envía a la estación de tierra y actúa sobre los elementos mecánicos, a petición del usuario.  
   
### 1.3	La estación de tierra    
Está compuesta por otro microprocesador Arduino y un portátil al que se conecta por USB. El microprocesador hace de intermediario entre el satélite y el portátil. Entrega al portátil los mensajes que recibe del satélite y envía al satélite los comandos que introduce el usuario a través del portátil. También procesa la información que llega del satélite, por ejemplo, para encender alarmas (leds de diferentes colores) en caso necesario. Lógicamente, también tiene incorporados los componentes necesarios para la comunicación con el satélite. El módulo Arduino está programado en C.   
   
La aplicación que se ejecuta en el portátil está programada en Python. Debe tener una interfaz de usuario cara y visualmente agradable. Debe permitir presentar al usuario los datos que se reciben (por ejemplo, una gráfica que muestre la evolución de la temperatura a lo largo del tiempo). También debe permitir al usuario enviar órdenes al satélite (por ejemplo, girar 90º el sensor que mide la proximidad de objetos).   
   
### 1.4	Comunicación 
La comunicación entre la estación de tierra y el satélite utiliza la tecnología LoRa (Long Range). Se trata de una tecnología de comunicación inalámbrica (como también lo son WiFi y Bluetooth), que es especialmente adecuada para comunicaciones a grandes distancias. No obstante, durante buena parte del desarrollo del proyecto, por cuestiones de comodidad y evitación de interferencias, la comunicación se realizará mediante cable.  
   
### 1.5	Demostración   
El siguiente vídeo es un ejemplo del resultado final en funcionamiento, elaborado por alumnos de cursos anteriores.    
   
[![](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DnBh4BNyI6vw)](https://www.youtube.com/watch?v=nBh4BNyI6vw)
   
### 1.6	Versiones
Deben implementarse cuatro versiones del sistema satelital, de complejidad creciente. Las características esenciales de cada versión se describen a continuación, aunque los requerimientos precisos se describen en próximos apartados de esta guía y las fechas de entrega se especificarán en el plan de la asignatura.  
   
<ins>Versión 1</ins>  
   
El satélite capta periódicamente los datos que ofrece el sensor de temperatura y humedad y los envía a tierra con la frecuencia establecida. El subsistema de tierra los recibe y los muestra en consola.   
   
El satélite también procesa mínimamente los datos captados (por ejemplo, calculando medias que también envía a tierra).
Además de mostrarlos en consola, la estación de tierra procesa los datos recibidos (por ejemplo, muestra una alarma en el caso de una secuencia alarmante de datos de temperatura).    
   
<ins>Versión 2</ins>    
   
El satélite dispone de un sensor de ultrasonidos que le permite captar datos de proximidad de objetos que pueden dañar al satélite y también los envía a tierra, junto con los datos indicados en la descripción de la versión 1.   
   
La estación de tierra muestra ahora los datos en forma de gráficas lo más claras e informativas posibles, incluyendo las alarmas establecidas en la versión 1. La estación de tierra también dispone de los elementos que le permiten al usuario enviar órdenes al satélite que modifiquen la tarea que realiza (por ejemplo, detener el envío de algunos de los datos o modificar las frecuencias de envío).  
   
Adicionalmente, el sensor de ultrasonidos puede estar montado sobre una plataforma que puede girar movida por un servo-motor. Desde la estación de tierra el usuario debe poder modificar la orientación del sensor de ultrasonidos enviando órdenes que hagan que el controlador actúe sobre el servo-motor.   
   
<ins>Versión 3</ins>    
   
El satélite dispone de un mecanismo que le permite obtener la posición exacta en la que se encuentra dentro de la órbita que recorre. El controlador enviará a tierra esa información periódicamente, junto a los datos ya descritos en las versiones anteriores.   
   
El controlador guarda en ficheros algunos datos de manera que puedan ser recuperados cuando los solicite la estación de tierra.  
    
La estación de tierra muestra al usuario la posición del satélite en cada momento, usando los mapas más adecuados. Además, también guarda en ficheros los datos recibidos y los recupera a petición del usuario. Todo ello debe poder gestionarse de forma cómoda desde la interfaz gráfica de la estación de tierra.   
   
<ins>Versión 4</ins>     
   
La última versión debe incluir todas las funcionalidades adicionales que elija el equipo, en función de su motivación y tiempo disponible. Naturalmente, se esperan funcionalidades espectaculares y sorprendentes.   
   
En las fechas indicadas en la planificación de la asignatura, cada grupo debe entregar el código correspondiente a la versión que se entrega junto con un vídeo de no más de 3 minutos que muestre que el código satisface los requisitos de la versión que se está entregando.   
   
### 1.7	Calificación    

La calificación del proyecto tiene un peso del 40% en la nota final de la asignatura. Esa calificación se obtiene de la siguiente forma:  

•	Calidad del producto final: 30%   
•	Resultados individuales de los exámenes de conocimiento del proyecto: 5%   
•	Resultados grupales de los exámenes de conocimiento del proyecto: 5%   
   
La calidad del producto final se valorará utilizando los criterios que se indican en la tabla siguiente.    
   
| Criterio  | Descripción | Peso |
| ------------- | -------------  | ------------- |
| Correcto |El prototipo realiza correctamente todas las funciones especificadas en los requisitos (la lista completa de esas funcionalidades se proporcionará durante el curso)  |40% 
| Robusto |El sistema resiste sin bloquearse los fallos que puedan producirse (por ejemplo, errores del usuario al interactuar con el sistema o fallos en los sensores del satélite) |7.5% |
| Amigable |El usuario no tiene dudas al interactuar con el sistema a través de la interfaz gráfica, que es, además, visualmente agradable.  |7.5% |
| Organizado y documentado	 |El código del controlador y de la estación de tierra está bien organizado en funciones. Además, se han añadido comentarios adecuados que deben permitir a otras personas, con poco esfuerzo, entender el código y hacer modificaciones si son necesarias	  |10% |
| Eficiente |El código usa siempre los algoritmos más adecuados para realizar las operaciones  |5% |
| Sorprendente |Las funcionalidades adicionales son interesantes, complejas y sorprendentes.	  |20% |
| Bien presentado	 |El vídeo que acompaña a la versión final presenta claramente el funcionamiento del sistema y resulta espectacular  |10% |
| TOTAL |  |100% |


Durante el curso se realizarán dos exámenes de conocimientos del proyecto, coincidiendo con la entrega de dos de las versiones antes descritas. Estos exámenes son individuales y se realizan en clase. Consisten en la realización, en el tiempo indicado, de una sencilla modificación del código del sistema desarrollado por el grupo. Un ejemplo de enunciado de un examen de conocimiento de proyecto puede ser este:   
 
_Añade a la interfaz gráfica de la estación de tierra un botón que haga que los datos de humedad se envíen cada segundo.
Cada examen se calificará con un 10 si durante el tiempo previsto se pone en evidencia que se ha resuelto bien el reto. La calificación será 0 en caso contrario._   
   
La media de las dos notas individuales obtenidas por cada alumno tendrá un peso del 5% en la nota del proyecto de ese alumno. La media de TODAS las notas de los miembros del grupo tendrá un peso de 5% en la nota del proyecto de cada miembro.   

## 3. Puesta en marcha de Arduino
### 3.1 Qué es Arduino 
Arduino es una plataforma de hardware y software de código abierto que fue creada en 2005 por un grupo de ingenieros y académicos italianos. Permite desarrollar proyectos de electrónica y automatización de forma sencilla. Consiste en placas electrónicas con microcontroladores programables y un entorno de desarrollo (Arduino IDE) basado en C/C++. Su popularidad se debe a su facilidad de uso, amplia comunidad y compatibilidad con sensores, motores, pantallas y módulos de comunicación, lo que la hace ideal para proyectos de robótica, IoT y educación en programación y electrónica.    

Existen varios modelos de Arduino. En la figura se muestran los elementos que contiene una placa Arduino UNO.   
<img src="https://github.com/user-attachments/assets/8cbf5de4-cb9f-4b2a-abee-75118dca86c5" width="400" height="300">  


El elemento fundamental es el microprocesador que puede generar señales al exterior a través de los pines de salida (por ejemplo, encender un led o mover un servo motor) y recibir información de exterior a través de los pines de entrada (por ejemplo, recibir datos de un canal de comunicación serie).     
    
### 3.2 Instalación de Arduino IDE
Para programar Arduino necesitas instalar el entorno de desarrollo integrado (IDE) de Arduino. Sigue los siguientes pasos para instalar Arduino IDE en tu ordenador:   
1.	Descarga el instalador de Arduino IDE desde la página oficial de Arduino: https://www.arduino.cc/en/software
(para windows, descarga el instalador de MSI Installer)
2. Ejecuta el instalador y sigue las instrucciones del asistente de instalación. Es importante marcar la opción de “Install USB driver” para que el sistema operativo pueda reconocer la placa Arduino.

### 3.3 Configuración de Arduino IDE
Una vez instalado Arduino IDE, es necesario configurar el entorno para que pueda detectar la placa Arduino. Sigue los siguientes pasos para configurar Arduino IDE:
1.	Abre Arduino IDE. Verás una ventana con un editor de texto y una barra de menús.
2.	Si queremos cambiar el idioma a español, selecciona la opción “File” en la barra de menús y luego “Preferences”. En la ventana de preferencias, busca la opción “Language” y selecciana “Español” en el menú desplegable.
3.	En los iconos laterales a la izquierda, seleccionamos el segundo, el correspondiente al Gestor de Placas. En el buscador, escribimos “Arduino AVR Boards” y pulsamos “Instalar”. Es posible que este tipo de placa ya esté instalada, en ese caso no es necesario instalarla de nuevo.
4.	Conecta la placa Arduino al ordenador mediante un cable USB. Una vez alimentada, se encenderá un led verde en la placa.
5. En la barra de menús, selecciona la opción “Herramientas” y luego “Placa”. Seleccionamos “Arduino AVR Boards” y luego “Arduino Uno”.
6.	En la misma barra de menús, selecciona la opción “Herramientas” y luego “Puerto”. Alli deberías ver una lista de puertos serie disponibles. Selecciona el puerto serie correspondiente

### 3.4 Primer programa en Arduino
Para comprobar que Arduino IDE está correctamente configurado, vamos a cargar un programa de ejemplo en la placa Arduino. Sigue los siguientes pasos para cargar el programa “Blink” en la placa Arduino:
```
void setup() {
   pinMode(13, OUTPUT);
}
void loop() {
   digitalWrite(13, HIGH);
   delay(1000);
   digitalWrite(13, LOW);
   delay(1000);
}
```

Fijaros que los programas de Arduino no tienen una función _main()_. En su lugar, tienen dos funciones: _setup()_ y _loop()_. La función _setup()_ se ejecuta una vez al inicio del programa, mientras que la función _loop()_ se ejecuta continuamente en un bucle.   
  
En este caso, la función _setup()_ configura el pin 13 como una salida digital. La función _loop()_ enciende y apaga el pin 13 cada segundo. Este pin está conectado a un led en la placa Arduino (de color amarillo), por lo que veremos el led parpadear cada segundo.    
  
Para cargar el programa en la placa Arduino simplemente pulsamos el segundo icono de la barra de herramientas, el de la flecha hacia la derecha, correspondiente a la función de “Cargar”. Si todo ha ido bien, veremos un mensaje indicando que la carga se ha completado en la parte inferior de la ventana y veremos el led parpadear. Tenemos entonces la placa y el IDE bien configurado y podemos empezar a dar los pasos de la primera versión del proyecto.   

## 4. Versión 1
En esta sección hay una guía paso a paso para el desarrollo de la versión 1 del proyecto (el resto de versiones no están tan guiadas). Durante el desarrollo de esta versión conviene que los miembros del equipo trabajen codo con codo, para ayudarse mutuamente en la comprensión de lo que se está haciendo. No es momento aún de repartir el trabajo entre los miembros del equipo. Ya llegará ese momento en las siguientes versiones.   
  
### Paso 1: Led rojo
Un led es un elemento muy simple que tiene dos patillas. La patilla larga se denomina ánodo y la corta cátodo. La corriente entre por el ánodo y según su intensidad ilumina el led con más o menos brillo. Si colocamos en el ánodo una tensión de 5V, que es la que proporciona un pin de salida de arduino, y conectamos el cátodo a tierra (0V) entonces la intensidad será muy alta y quemaremos el led. Para limitar la intensidad a valores operativos hay que colocar una resistencia de unos 220 omnios (más sobre estas cuestiones se estudia en asignaturas de electrónica). El esquema del montaje necesario se muestra en la figura.

 <img src="https://github.com/user-attachments/assets/28247ec4-5b2d-4947-a593-392dcd4628ad" width="400" height="300" />

Con ese montaje, el led se encenderá de manera permanente porque siempre tiene 5V en el ánodo. Si queremos poder encender y apagar el led por programa, tenemos que conectar el ánodo no a 5V sino a uno de los pines de salida de Arduino (por ejemplo el 12).  Ahora, el mismo programa que encendía y apagaba con el pin 13 el led amarillo que tiene la placa Arduino sirve para encender y apagar nuestro led rojo, si cambiamos el 13 por el 12. Compruébalo.    

### Paso 2: Alternar la iluminación de dos leds
Queremos encencer/apagar dos leds: el amarillo (conectado al pin 13)  y el rojo (conectado al pin 12) pero con periodos distintos, por ejemplo, el amarillo cada 2 segundos y el rojo cada 3.   
 
Ahora ya no es tan fácil decidir cómo es el programa que hace eso, dónde colocar la operación delay y cuantos milisegundos debe esperar. Y la  cosa se complicará mucho más cuando nuestro programa tenga que hacer otras muchas tareas, con periodos diferentes (cosa que pasará muy pronto).    
 
Para resolver esta cuestión usaremos un enfoque diferente para nuestros programas. Observad el código siguiente.    
```
const int led1 = 13;  // LED en el pin 13 (Amarillo)
const int led2 = 12;  // LED en el pin 12 (Rojo)

int nextMillis1;
int nextMillis2;
const long interval1 = 2000; // 2 segundos para el LED 13
const long interval2 = 3000; // 3 segundos para el LED 12

bool stateLed1 = LOW;
bool stateLed2 = LOW;

void setup() {
    pinMode(led1, OUTPUT);
    pinMode(led2, OUTPUT);
    // primer instante en el que habrá que cambiar
    nextMillis1 = millis() + interval1;
    nextMillis2 = millis() + interval2;
}

void loop() {
    // Control del LED en el pin 13 (2 segundos)
    if (millis() >= nextMillis1) {
        // Ya toca cambiar
        if (stateLed1 == LOW)
             stateLed1 = HIGH;
        else
             stateLed1 = LOW;
        digitalWrite(led1, stateLed1);
        // Siguiente instante en el que habrá que cambiar
        nextMillis1 = millis() + interval1;
    }

    // Control del LED en el pin 12 (3 segundos)
    if (millis() >= nextMillis2) {
       if (stateLed2 == LOW)
             stateLed2 = HIGH;
        else
             stateLed2 = LOW;
        digitalWrite(led2, stateLed2);
        nextMillis2 = millis() + interval2;
    }
}
```
 
El programa es fácil de entender. La función _millis()_ nos da el número de milisegundos que han pasado desde que se inició el programa. Nos proporciona, por tanto, una referencia del instante de tiempo actual. La variable _nextMillis1_ nos dice en qué instante toca cambiar el led amarillo. Por tanto, el bucle solo tiene que comprobar que ya hemos llegado a ese instante, entonces cambia el led y calcula el nuevo instante en el que habrá que volver a cambiar. Lo mismo hacemos con el led rojo.  
  
Con esta estructura es muy fácil añadir más tareas periódicas a nuestro programa. Por ejemplo, probad a añadir un led verde que se encienda/apague cada 5 segundos.    

AQUÍ ES INTERESANTE QUE EXPERIMENTEN EL PROBLEMA QUE SE PRODUCE CUANDO TIENEN EL PROGRAMA FUNCIONANDO UN RATO DE  MANERA QUE SE DESBORDAN LAS VARIABLES mextMillis, QUE SON DE TIPO int Y DEBERIAN SER DE TIPO unsigned long. AUNQUE INCLUSO EN ESE CASO, SI EL SATELITE VA A ESTAR FUNCIONANDO AÑOS, ACABARÁ DESBORDANDOSE.
PUEDE SER INTERESANTE QUE OBSERVEN CUÁNTO TARDA EN DESBORDARSE UN INT, PREDECIR CUÁNTO TARDARÍA EN DESBORDARSE UN INSIGNED LONG Y CUAL SERÍA LA SOLUCIÓN DEFNITIVA AL PROBLEMA.    

### Paso 3: Comunicación entre Arduino y el portátil
La placa Arduino está conectada a un puerto USB de tu portátil. Esa es una comunicación serie que utiliza el protocolo UART (Universal Asynchronous Receiver/Transmitter). En el paso X aprenderás más sobre este protocolo, que también se usará para conectar por cable el arduino satélite con el arduino de tierra.  
  
Esta comunicación serie por cable entre el portátil y la placa Arduino ya se ha estado usando para que el IDE que se ejecuta en tu portátil pueda enviar el código compilado de tu programa a la placa, donde se va a ejecutar. Ahora vamos a aprender a usar ese mismo canal de comunicación para que el programa que se ejecuta en la placa pueda enviar mensajes al IDE de manera que éste pueda mostrarlos al usuario.    
   
Fíjate en el programa siguiente:
```
int i=0;
void setup() {
   Serial.begin(9600);
}
void loop() {
   Serial.println(i);
   i++;
   delay(1000);
}
```
Este programa envía un número entero cada segundo a través del puerto serie a una velocidad de 9600 baudios (bits por segundo), que es la velocidad configurada en la función _setup()_. Para ver en tu portátil los datos recibidos, puedes abrir el monitor serie en Arduino IDE seleccionando la opción “Herramientas” ‑> “Monitor Serie” o seleccionado el icono de la lupa en la barra de herramientas.   
 
Prueba ahora a modificar el programa que gestiona los dos leds para añadirle una nueva tarea que consista en escribir en el Monitor serie la frase “Aún sigo aquí”, cada 10 segundos.    
 
### Paso 4: Sensor de temperatura
Vamos a conectar ahora al Arduino un sensor de temperatura y humedad. A diferencia del led, cuya operación requiere una señal de salida de Arduino, el sensor de temperatura nos proporciona una señal de entrada que codifica la temperatura y humedad captadas. Utilizaremos el sensor DHT11, que tiene un rango de medición de temperatura de 0 a 50 grados Celsius y un rango de medición de humedad de 20% a 90%.   
 
La figura muestra cómo conectar el sensor a la placa Arduino.    

<img  src="https://github.com/user-attachments/assets/b634d33d-6cf3-428c-9f74-108bd98d5d9e" width="400" height="300"/>
 
El sensor DHT11 envia la información a la placa a través del cable verde, que está conectado al pin 2.  La comunicación se realiza mediante un protocolo llamado One‑Wire que solo necesita un cable para transmitir la información.  
 
Existe ya una librería de Arduino que facilita la comunicación con el sensor DHT11. Para instalar la librería, selecciona el tercer icono de la barra lateral de herramientas, el correspondiente a “Gestor de bibliotecas”. En el buscador, escribe “DHT” y pulsa “Instalar” en la librería “DHT sensor library by Adafruit”.    
 
Una vez instalada la librería, puedes utilizarla en tus programas de Arduino. A continuación tienes un ejemplo de programa que lee la temperatura y la humedad del sensor DHT11 cada 2 segundos y las muestra en el monitor serie:    
```
// Definiciones necesarias
#include <DHT.h>
#define DHTPIN 2
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);
void setup() {
   Serial.begin(9600);
   // Inicialización del sensor
   dht.begin();
}
void loop() {
   delay(2000);
   float h = dht.readHumidity();
   float t = dht.readTemperature();
   if (isnan(h) || isnan(t))
      Serial.println("Error al leer el sensor DHT11");
   else {
      Serial.print("Humedad: ");
      Serial.print(h);
      Serial.print("%\t");
      Serial.print("Temperatura: ");
      Serial.print(t);
      Serial.println("°C");
   }
}
```
La función _dht.readHumidity()_ devuelve la humedad en porcentaje, y la función _dht.readTemperature()_ devuelve la temperatura en grados Celsius. Si no se puede leer la humedad o la temperatura, las funciones devuelven NAN (Not A Number). _isnan()_ es una función que comprueba si un número es NAN. _\t_ es un carácter de tabulación, que nos permite alinear los datos en el monitor serie. Fíjate cómo escribimos en el monitor serie una frase por partes, como por ejemplo: "Humedad: 25%   Temperatura: 30ºC". La función _Serial.println()_: introduce al final de la frase el caracter de fin de línea.   
 
Incorpora ahora al programa que controla los dos leds una nueva tarea que captura los datos del sensor cada 5 segundos los envía por el canal serie para que se muestren en el monitor serie.   

### Paso 5: Test unitario
A medida que se avance en el proyecto vais a tener más líneas de código, más dispositivos en las placas Arduino y más cables. Además, con frecuencia tendréis que poner/quitar dispositivos y cables (por ejemplo, para recogerlo todo al acabar la jornada y volver a montarlo todo el siguiente día). Es, por tanto, bastante probable que algo que funcionaba ayer no funcione bien hoy porque falta algún cable, por ejemplo. Y claro, cuando hay un montón de código, dispositivos y cables no va a ser nada fácil encontrar dónde está el fallo.    
 
Para enfrentarse a ese reto es esencial disponer de una colección de programas de test unitario. Un test unitario es un programa que pone a prueba una parte muy específica del sistema para comprobar si funciona correctamente o no. Vuestro primer test unitario puede ser un programa que verifique que el sensor de temperatura está capturando correctamente los datos. Con lo que habéis aprendido en el paso anterior podéis preparar vuestro test unitario para el sensor de temperatura, que os vendrá muy bien en caso de crisis para descartar (o confirmar) que el problema sea el sensor.   

### Paso 6: Enlace de comunicación entre dos arduinos
Como es natural, la comunicación entre el arduino satélite y el arduino tierra se realizará de forma inalámbrica, para lo cual se necesitará el kit LoRa. Sin embargo, por comodidad, en las primeras versiones el enlace de comunicación será por cable. En cualquiera de los dos casos, la comunicación utilizará el protocolo de comunicación serie UART.   
 
Como puede verse en la siguiente figura, para comunicar dos dispositivos mediante el protocolo UART solo se necesitan tres cables. El device 1 envía los bits al devide 2 por el cable rojo (salida TX del device 1 y entrada RX del 2) y recibe los bits por el verde. Ambos dispositivos deben tener una referencia común que proporciona el cable negro (GND).   
<img  src="https://github.com/user-attachments/assets/c38dd31f-8e4d-472e-bdf4-06dc669fda68" width="400" height="150"/>
  
La figura siguiente muestra un diagrama de tiempos que ilustra cómo funciona la comunicación.   

<img  src="https://github.com/user-attachments/assets/c1e4ff4d-1efe-4d55-9746-4d67722b8bf3" width="400" height="100"/>
 
Imagina que estamos observando el cable rojo por que el viajan los bits del device 1 al devide 2. En el estado de reposo (idle) el cable está a 5V (un bit a 1). Para empezar la transmisión el cable se pone a 0. A partir de ahí se envían los 8 bits que conforman el byte que se quiere transmitir (un byte puede codificar, por ejemplo, una letra). Finalmente, el cable vuelve a 1 y se queda en estado idle hasta que haya que transmitir el siguiente byte. Como es lógico, la frecuencia a la que el transmisor envía los bits debe ser la misma que la frecuencia a la que el receptor los muestrea. En el ejemplo de la figura, si el receptor muestrea el doble de rápido interpretará que está recibiendo la secuencia “11001100..”.   
 
El montaje más simple que se necesita para experimentar la comunicación serie por cable es el que se muestra en la figura siguiente.

 <img  src="https://github.com/user-attachments/assets/01d9d53e-5bb3-4b14-99f1-6ed7008cfdf2" width="400" height="250"/>

Los dos Arduinos están conectados al mismo portátil (cada uno a un puerto USB diferente). Tenemos por tanto dos IDE en marcha en el portátil, cada uno ocupándose de uno de los Arduinos. En ambos Arduinos el pin 10 actua como señal RX y el pin 11 como señal TX y están conectados también mediante la señal GND.   
 
El programa más simple para transmitir información del Arduino transmisor (por ejemplo, device 1) al receptor (device 2) se muestra a continuación.   
```
#include <SoftwareSerial.h>
int i;
SoftwareSerial mySerial(10, 11); // RX, TX 
void setup() {
   mySerial.begin(9600);
   mySerial.println("Empezamos");
   i=1;
}
void loop() {
   delay (3000);
   mySerial.print("Envío: ");
   mySerial.println(i);
   i=i+1;
}
```

La librería que facilitará la comunicación es _SoftwareSerial_, que ya está instalada por defecto. El programa transmisor crea un canal de comunicación serie que llama _mySerial_ y le indica qué pines debe usar como RX (pin 10) y como TX (pin 11). En la función _setup_ establece la velocidad de comunicación de ese canal (9600 baudios) y se envía ya un primer mensaje de aviso. La función _loop_ enviará con ese canal, cada 3 segundos, serie la frase “Envío n”, siendo n un número del 1 en adelante. Por el canal de comunicación viajarán bit a bit los códigos ASCII de cada uno de los caracteres de la frase, incluido el carácter de fin de línea que se añade automáticamente por el hecho de haber usado la función _println_.   
 
El programa que debe ejecutar el Arduino receptores el siguiente:   
```
#include <SoftwareSerial.h>
SoftwareSerial mySerial(10, 11); // RX, TX (azul, naranja)
unsigned long nextMillis = 500;
void setup() {
   Serial.begin(9600);
   Serial.println("Empezamos la recepción");
   mySerial.begin(9600);
}
void loop() {
   if (mySerial.available()) {
      String data = mySerial.readString();
      Serial.print(data);
   }
}
```
El receptor también va a usar la libreria _SoftwareSerial_. Crea el canal _mySerial_ para las comunicaciones serie, también usando los pines 10 y 11 como RX y TX respectivamente, y especifica la velocidad de comunicación, que debe coincidir con la establecida por el transmisor.
 
La función _mySerial.available()_ indica si se han recibido nuevos bytes por el canal serie. En caso afirmativo se leen todos los bytes hasta el carácter de fin de línea, usando la función _mySerial.readString()_.

Puesto que queremos que la frase recibida se pueda ver el monitor serie del IDE conectado al arduino receptor, el programa usa también el canal _Serial_, tal y como se vio en el paso 3. Fíjate que para escribir en el monitor serie la frase recibida el programa receptor usa la función _Serial.print(data)_ y no _Serial.println(data)_, que es lo que cabría esperar. ¿Por qué?.   

Llegados a este punto, es fácil añadir a los programas del transmisor y del receptor el código necesario para que haya comunicación en ambos sentidos. Por ejemplo, el receptor puede enviar una frase de agradecimiento al transmisor cada vez que recibe un nuevo mensaje. Naturalmente, el transmisor enviará la frase recibida al monitor serie del IDE correspondiente. 
Preparad esos códigos y probadlos. El resultado puede ser vuestro segundo test unitario que os permitirá verificar, en caso de necesidad, que la comunicación entre los arduinos funciona correctamente. Como es lógico, ahora no tiene sentido hablar de un arduino transmisor y otro receptor puesto que ambos transmiten y reciben.   
HABLAMOS AQUI YA DE COMO USAR EL CANAL HARDWARE EN VEZ DEL SOFTWARE PARA EVITAR LOS PROBLEMAS QUE VIMOS CUANDO INCORPOREN EL SERVO??

### Paso 7: Recepción de datos en la interfaz Python
En el paso anterior hemos visto cómo los datos que envía un Arduino llegan, a través del canal serie, hasta el portátil conectado al segundo Arduino. Los datos llegan hasta el IDE conectado al Arduino receptor y se muestran en el monitor serie correspondiente.   
 
Sin embargo, lo que realmente nos interesa es que los datos lleguen a nuestro programa en Python que será la interfaz gráfica con el usuario. Por tanto, el programa en Python también debe poder leer los datos que se reciben por el canal serie.   
 
El código Python necesario para hacer esto es el siguiente:   
```
import serial
device = 'COM3'
mySerial = serial.Serial(device, 9600)
while True:
   if mySerial.in_waiting > 0:
      linea = mySerial.readline().decode('utf-8').rstrip()
      print(linea)
```
El programa identifica el puerto serie que debe usarse (el mismo COM al que está conectado el Arduino receptor). Después configura el canal de comunicación serie, con la velocidad adecuada. Luego entra en un bucle infinito en el que pregunta si se han recibido datos y en caso afirmativo lee toda la frase recibida y la escribe en consola. La lógica del programa es la misma que la del programa que ejecuta el Arduino receptor que se ha visto en el paso anterior.    
 
Para que este programa funcione es necesario instalar en el intérprete de Python la librería _myserial_.   
 
Muy probablemente, al ejecutar el programa se producirá un error porque el programa no puede usar el puerto serie específicado. Eso se produce en el caso de que en ese momento esté activo el monitor serie del IDE conectado al Arduino receptor. Puesto que el puerto serie está ocupado por el monitor serie, el programa en Python no puede usarlo. El problema se resuelve cerrando el monitor serie, con lo cual el puerto serie queda libre para que pueda ser usado por el programa Python.    
 
Quizá ahora es buena idea añadir algo más de código al test unitario de comunicaciones para verificar también que los datos llegan correctamente al programa e Python.   
 
### Paso 8: Presentar los datos de temperatura y humedad al usuario
Tenemos ya encima de la mesa todos los elementos necesarios para construir un sistema en el que el Arduino satélite capte los datos de temperatura y humedad y los envíe a tierra (por cable) cada 3 segundos, de manera que esos datos aparezcan en la consola del programa en Python para que pueda verlos el usuario. Además, el Arduino satélite debe tener un led verde que se encienda durante un breve instante cada vez que se envían datos y el Arduino de tierra también un led verde que se enciende cada vez que recibe nuevos datos.    

### Paso 9: Una gráfica dinámica con los datos de temperatura
La forma ideal de presentar al usuario los datos de temperatura es mediante una gráfica que muestre cómo evolucionan esos datos a lo largo del tiempo. Para ello podemos usar la librería _matplotlib_ de Python. Veamos cómo hacerlo.   
  
Para empezar, haremos que el satélite envíe los datos en un formato que resulte fácil de procesar en tierra. Por ejemplo, el mensaje podría ser:    
 
_“T:34,2:H:20”_    
 
Este formato tiene la ventaja de que ocupa menos bytes (menos saturación en el canal de comunicación). La segunda ventaja es que cuando el programa Python reciba el mensaje podrá hacer la siguiente operación:    
 
_trozos = mensajeRecibido.Split (‘:’)_   
 
De esta operación se obtiene una lista de 4 trozos. El dato de temperatura que queremos mostrar en la gráfica (34,2 en el ejemplo anterior) está en _trozos[1]_ y el de humedad (20) en _trozos[3]_.   
 
En el vídeo siguiente se muestra cómo incorporar una gráfica al programa en Python que muestre de manera dinámica los datos de temperatura que se van recibiendo.    

[![](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D_fIoPHwnay0)](https://www.youtube.com/watch?v=_fIoPHwnay0)
   

### Paso 10: Una interfaz gráfica más amigable
El programa Python debe presentar al usuario una interfaz gráfica lo más amigable posible (con botones, colores, etc.). Aunque de momento la interacción entre el programa Python y el usuario es mínima, vamos a ver ya cómo crear una interfaz gráfica más amigable a la que iremos añadiendo funcionalidades a medida que vayan aumentando las necesodades de interacción con el usuario.   
 
Para hacer la interfaz gráfica usaremos la librería Tkinter, que ya viene por defecto incorporada al intérprete de Python. El programa siguiente crea la interfaz gráfica que se muestra en la figura.   
```
from tkinter import *

def EntrarClick ():
    print ('Has introducido la frase --- ' + fraseEntry.get() + ' --- y has pulsado el botón entrar')

def AClick ():
    print ('Has pulsado el botón A')

window = Tk()
window.geometry("400x400")
window.rowconfigure(0, weight=1)
window.rowconfigure(1, weight=1)
window.rowconfigure(2, weight=1)
window.columnconfigure(0, weight=1)
window.columnconfigure(1, weight=1)
window.columnconfigure(2, weight=1)
window.columnconfigure(3, weight=1)

tituloLabel = Label(window, text = "Mi programa", font=("Courier", 20, "italic"))
tituloLabel.grid(row=0, column=0, columnspan=5, padx=5, pady=5, sticky=N + S + E + W)

fraseEntry = Entry(window)
fraseEntry.grid(row=1, column=0, columnspan = 3, padx=5, pady=5, sticky=N + S + E + W)

EntrarButton = Button(window, text="Entrar", bg='red', fg="white",command=EntrarClick)
EntrarButton.grid(row=1, column=3, padx=5, pady=5, sticky=N + S + E + W)

AButton = Button(window, text="A", bg='red', fg="white",command=AClick)
AButton.grid(row=2, column=0, padx=5, pady=5, sticky=N + S + E + W)
BButton = Button(window, text="B", bg='yellow', fg="black")
BButton.grid(row=2, column=1, padx=5, pady=5, sticky=N + S + E + W)
CButton = Button(window, text="C", bg='blue', fg="white")
CButton.grid(row=2, column=2, padx=5, pady=5, sticky=N + S + E + W)
DButton = Button(window, text="D", bg='orange', fg="black")
DButton.grid(row=2, column=3, padx=5, pady=5, sticky=N + S + E + W)

window.mainloop()
```
<img  src="https://github.com/user-attachments/assets/0b2ad25e-4c7f-4717-9e8a-a44bcbc6b3d1" width="200" height="200"/>

Aunque el código parece muy aparatoso, en realidad es muy sencillo. Conviene imaginar que la interfaz gráfica es una matriz de 3 filas y 5 columnas. Eso es exactamente lo que indicamos al principio del código. Después definimos los elementos que deben colocarse en cada una de las posiciones de esa matriz. Por ejemplo, el botón _A_ se coloca en la fila 2, columna 0. Además, indicamos el color que debe tener el botón y el texto que debe mostrarse.   
   
Algunos elementos ocupan más de una casilla de la matriz. Por ejemplo, el cuadro de texto llamado _fraseEntry_ se coloca en la fila 1, columna 0 pero se expande 3 columnas, y la etiqueta _tituloLabel_ se coloca en la fila 0, columna 0 y ocupa las 5 columnas.    
 
El parámetro _command_ es el que indica la función que hay que ejecutar cuando se pulsa el botón. En el ejemplo anterior solo los botones _A_ y _Entrar_ tienen asociada una función.    

Ejecuta el programa anterior y experimenta un poco con colores, posiciones y tamaños de botones y con las funciones asociadas a los botones.   

 





