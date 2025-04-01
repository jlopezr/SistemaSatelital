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
En esta sección hay una guía paso a paso para el desarrollo de la versión 1 del proyecto (el resto de versiones no están tan guiadas). Se recomienda fuertemente que cada miembro del grupo realice esos pasos de forma individual y que consulte las dudas con sus compañeros (o con los profesores si se está trabajando en el aula). Puesto que algunos pasos requieren el uso de dos Arduinos, en esos pasos tendréis que compartir recursos y hacelos juntos. En todo caso, no es momento aún de repartir el trabajo entre los miembros del equipo. Ya llegará ese momento en las siguientes versiones.   
  
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

 
### Paso 11: Parar y reanudar la transmisión de datos de temperatura
Una de las funcionalidades que debe tener la interfaz gráfica es permitir al usuario parar y reanudar en el envio por parte del satélite, de los datos de temperatura y humedad. Esa será la primera funcionalidad que vamos a incorporar a nuestra interfaz gráfica.   

Prepara una interfaz gráfica en Tkinter que tenga 3 botones, que llamaremos _Iniciar_, _Parar_ y _Reanudar_. El botón _Iniciar_ se usará para iniciar la recepción de datos de humedad y temperatura. Cuando pulsemos ese botón debería mostrarse ya la gráfica con la evolución de la temperatura a lo largo del tiempo, como hemos hecho en el paso 9. El  botón _Parar_ se usará para enviar al satélite la orden de que detenga el envio de datos de humedad y temperatura. Finalmente el botón _Reanudar_ se usará para enviar al satélite la orden de reanudar el envío de datos.   

Además del uso de una interfaz gráfica, la novedad más importante de este paso es el envío de un mensaje desde el programa Python al Arduino satélite. Se enviará la palabra 'Parar' o la palabra 'Reanudar' según el botón que pulse el usuario. Esas operaciones son muy sencillas. Por ejemplo, el código que hay que ejecutar para enviar la palabra 'Parar' por el canal serie desde el programa en Python es:  
```
mensaje = "Parar"
mySerial.write(mensaje.encode('utf-8'))
```
Por otro lado, el código que hay que ejecutar cuando se pulse el botón para iniciar la recepción de datos es el siguiente (que ya vimos en el paso 7), asumiendo que se han realizado las inicializaciones necesarias:   
```
while True:
   if mySerial.in_waiting > 0:
      linea = mySerial.readline().decode('utf-8').rstrip()
      print(linea)
```
Recuerda que ese código escribe los datos en consola. Ya sabes bien cómo hacer para que se muestren en una gráfica de manera dinámica.   

El problema que se plantea es que si ejecutamos ese código al pulsar el botón _Iniciar_ la interfaz gráfica se va a quedar bloqueada ejecutando ese bucle infinito y no hará caso al usuario cuando pulse los botones _Parar_ o _Reanudar_. Para resolver ese problema tenemos que echar mano del mecanismo de concurrencia.   

Cuando estás trabajando con tu portátil tienes varios programas en marcha al mismo tiempo. Por ejemplo, puedes estar ejecutando el IDE conectado a un Arduino y al mismo tiempo estás usando un navegador para consultar al ChatGPT y quizá una aplicación de mensajería para chatear con tus colegas. La impresión que tienes es que el procesador del portátil está ejecutando todos esos programa al mismo tiempo, porque ninguno de ellos está bloqueado por culpa de la ejecución de otros. En realidad, el procesador está usando el mecanismo de la concurrencia.   

Lo que hace el procesador es ejecutar uno de esos programas durante un ratito (unos milisegundos), después le dedica otro ratito a otro de los programas y así va atendiendo durante unos milisegundos a todos los programas que tienes activos en tu portátil, hasta regresar al primero dedicarle unos pocos milisegundos más. Como el procesador hace todo eso de manera muy rápida, el usuario ni se entera del abandono que han ido sufriendo sus programas. Piensa que en el tiempo que tardas en decidir si pulsas el botón rojo o el azul, o mientras piensas qué le vas a pedir al ChatGPT el procesador tiene tiempo de dedicarle ese ratito a todos los programas activos.    

La cuestión es cómo usar el mecanismo de la concurrencia para que el procesador pueda atender  al bucle infinito que recibe los datos y al mismo tiempo ejecutar las ordenes correspondientes cuando el usuario pulse un botón. La cosa se resuelve haciendo que el bucle infinito se ejecute en un thread (hilo) independiente, tal y como muestra el código siguienete:   
```
threadRecepcion = threading.Thread (target = recepcion)
threadRecepcion.start()
```
Ese es el código que debe ejecutar la interfaz gráfica cuando el usuario pulsa el botón _Iniciar_. Se pone en marcha un nuevo thread que va a ejecutar la función _recepcion_ de manera concurrente con la interfaz gráfica, que ya no va a quedar bloqueada por culpa del bucle infinito, que ahora se pone en marcha en la función _recepcion_.    

El siguiente paso es retocar los códigos del Arduino de tierra para que transmita al satélite las ordenes de parar o reanudar que reciba de la interfaz gráfica. La cosa es muy sencilla. De la misma manera que el Arduino de tierra recibe mesajes de mySerial (del satélite) y los envía por Serial (a la interfaz gráfica), puede recibir también de Serial y enviarlos tal cual a mySerial. Añade las líneas de código necesarias al programa del Arduino de tierra que se mostró en el paso 6 (al que allí nos referíamos como Arduino receptor).   

El código para el Arduino satélite es algo más complicado. Se trata de añadir una variable booleana (solo puede valer _true_ o _false_) que indique si debe o no enviar los datos cuando llegue el momento de hacerlo. Supongamos que llamamos a esa variable _enviarDatos_, que inicialmente tendrá el valor _true_. Por otra parte, tiene que estar pendiente de los mensajes que puedan llegar por mySerial (procedentes del Arduino de tierra) de manera que si el mensaje recibido es "Parar" pondrá la variable _enviarDatos_ a _false_ y si llega el mensaje "Reanudar" volverá a poner la palabra a _true_. Trata de hacer estos cambios y comprueba que el sistema funciona correctamente.   

### Paso 12: Incrustar la gráfica dinámica en la interfaz gráfica
En la versión actual la gráfica dinámica de temperatura se muestra de manera independiente a la interfaz gráfica. Eso puede ser muy conveniente para poder arrastrar la gráfica al lugar mas conveniente de la pantalla de nuestro portátil.   

Pero también puede ser conveniente diseñar la interfaz gráfica de manera que cada gráfica (habrá verias) tenga un lugar asignado en esa interfaz. Para hacer esto tenemos que aprender a incrustar las gráficas en una interfaz gráfica Tkinter. Los vídeos siguientes muestran cómo hacerlo.   
 
[![](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DBnBhjilyvgw)](https://www.youtube.com/playlist?list=PL64O0POFYjHr0OWWax06x5CENZmxmfFec)

### Paso 13: Alarmas
En este último paso vamos a incorporar mecanismos de alarma que puedan señalar al usuario el mal funcionamiento del sistema. De momento consideraremos solo el caso de fallo en la captura de datos de humedad y temperatura y fallo en la comunicación entre el satélite y la estación de tierra. La alarma puede consistir simplemente en encender un led en el Arduino de tierra, que es el que estará a la vista del usuario (lógicamente, tendremos dos leds de colores diferentes para informar al usuario del tipo de alarma).       

Ya vimos en el paso 4 cómo detectar que el valor capturado de humedad o temperatura no es correcto. Lo que debemos resolver ahora es cómo avisar a la estación de tierra de tal circunstancia. Pero además, no vamos a avisar a la estación de tierra de manera inmediata. Conviene confirmar, antes de enviar la alarma, que los datos se están capturando mal durante algunos segundos (por ejemplo 5).   

El código que necesitamos en el Arduino satélite (que es el que detectará la anomalía) es el siguiente:  
```
 void loop() {
   // otras tareas
   if (millis() >= nextHT) {
      float h = dht.readHumidity();
      float t = dht.readTemperature();
      if (isnan(h) || isnan(t))
         esperandoTimeout = true;
         nextTimeoutHT = millis() + 5000; // 5 segundos
      else {
         esperandoTimeout = true;
         Serial.print("T: ");
         Serial.print(t);
         Serial.print(":H:");
         Serial.println(h);
      }
   }
   if (esperandoTimeout && (millis() >= nextTimeoutHT))
         Serial.print ("Fallo");
   // otras tareas
}
```
Si se produce un fallo al capturar la temperatura fijamos un tiempo límite (_nextTimeoutHT_) y si se alcanza este tiempo sin haber capturado correctamente la temperatura se envía la palabra "Fallo" a la estación de tierra.    

Ahora hay que retocar un poco el código del Arduino de tierra de manera que si recibe del satélite la palabra "Fallo" encienda el led correspondiente a este tipo de alarma. Naturalmente, también puede enviar el mensaje a la interfaz gráfica en la que podemos mostrar de alguna manera esa situación de alarma (por ejemplo, haciendo sonar una alarma auditiva por si en ese momento el usuario se ha dormido y no puede ver encenderse el led).    

El programa del Arduino de tierra tiene que incluir también el código necesario para detectar fallo de comunicación. Ese fallo se produce cuando pasa un cierto tiempo (por ejemplo, 5 segundos) sin recibir ningún mensaje del satélite. El mecanismo para implementar esta alarma puede ser muy similar al usado en el Arduino satelite para la alarma de temperatura incorrecta. Cuando el Arduino de tierra reciba un mensaje del satélite pondrá en marcha un mecanismo de timeout de 5 segundos. Si pasan esos 5 segundos sin haber recibido un nuevo mensaje del satélite encenderá el led correspondiente a ese tipo de alarma (e idealmente envía un mensaje a la interfaz gráfica para que se genere esa alarma sonora).   

Implementa estas alarmas y comprueba que funcionan bien, por ejemplo desconectando alguno de los cables del sensor de humedad o alguno de los cables de comunicación entre los dos Arduinos.    

### Entrega de la verión 1
Llegados a este punto ya podemos dar por concluida la versión 1 del proyecto. La lista siguiente es un resumen de lo que debería estar funcionando y puede servirte como lista de comprobación (recuerda que el término controlador se usa para referirnos al Arduino satélite).    
 
1. El controlador capta correctamente los datos de humedad y temperatura.
2. La estación de tierra recibe correctamente los datos que le envía el controlador y los muestra en una gráfica dinámica.
3. La gráfica dinámica está incrustada en la interfaz gráfica.
4. El usuario puede parar/reanudar el envío de los datos de humedad y temperatura
5. El controlador avisa correctamente a la estación de tierra en el caso de que no pueda captar bien los datos de temperatura y humedad (por ejemplo, porque se han desconectado los sensores).
6. La estación de tierra detecta un fallo en la comunicación con el controlador y avisa al usuario de esta circunstancia.
7. El usuario de la estación de tierra no tiene ninguna duda de como interactuar con la interfaz gráfica ni para interpretar correctamente la información que se muestra en consola (tanto los datos como las alarmas)
8. El código está bien estructurado e indentado. Es fácil localizar en que parte del código que hace cada una de las operaciones de la versión 1.
9. Se han añadido comentarios clarificadores.

En el caso de que cada miembro del grupo haya desarrollado su propia versión 1 del proyecto, es el momento de ponerse de acuerdo en cuál será el código con el que trabajará a partir de ahora todo el grupo para desarrollar las versiones siguientes.   

La entrega de la versión 1 tiene dos partes. Por una parte debe entregarse un fichero comprimido con los códigos, que debe incluir:   

* El código del Arduino satélite
* El código del Arduino de tierra
* El código de la interfaz gráfica
* En una carpeta adicional: los códigos de los test unitarios que hayais preparado.   

Por otra parte debe entregarse un vídeo de no más de 5 minutos que muestre el correcto funcionamiento del sistema (es decir, todo lo que indica la tabla anterior) y además muestre las partes más relevantes de los tres códigos, con énfasis especial en los códigos que no han sido producto de cortar de esta guía y pegar (por ejemplo, los códigos para incrustar la gráfica en la interfaz gráfica o para implementar las alarmas). Para mostrar el sistema en funcionamiento probablemente tendréis que hacer un vídeo compuesto por una captura de escritorio en la que se vea la aplicación en funcionamiento y otro vídeo sincronizado con este en el que vea el hardware en acción. La forma en entregar el vídeo es colocar la url (de youtube o google drive) correspondiente en el campo Observaciones de la tarea en la que se ha entregado el código.

HACEMOS QUE MANTENGAN UN REPOSITORIO EN GITHUB CON LAS DIFERENTES VERSIONES DEL PROYECTO Y QUE NOS VAYAN ENTREGANDO LA URL?
 
## 5. Versión 2
En la versión 2 vamos a incorporar al sistema un sensor de distancia que nos permitirá detectar la proximidad al satélite de objetos que puedan impactar con él. Además, añadiremos algo de computación para cálculo de medias de temperaturas.   
 
La versión 2 del proyecto está mucho menos guiada que la version 1. Además, empezará ya a ser necesario identificar tareas que puedan repartirse entre los miembros del grupo, para luego integrar los resultados y verificar el correcto funcionamiento de todo junto. En los apartados siguientes se describen los requisitos de la versión 2 y se dan algunas pautas que pueden ayudar a su implementación.    
 
### 5.1 Protocolo de aplicación
En la versión 2 (y siguientes) va a aumentar significativamente el número de tipos de mensajes que se intercambian el satélite y la estación de tierra. Por ejemplo, desde el satélite hacia la estación de tierra no solo viajarán los datos de temperatura y humedad sino valores medios de la temperatura o datos de distancia de objetos cercanos al satélite. Por otra parte, desde la estación de tierra al satélite ademas de órdenes para parar o reanudar la transmisión de datos de temperatura también viajarán ordenes para cambiar la periodicidad de los envíos de datos o para cambiar la orientación del sensor de distancias. Se hace necesario, por tanto, definir lo antes posible un sencillo protocolo de aplicación en el que se defina el formato de todos los tipos de mensajes que viajan de un sitio a otro.   

Lo más sencillo es que cada uno de los mensajes que se envían desde el satélite a tierra empiecen por un código que determine el tipo de información que lleva el mensaje. El código puede ser simplemente un número. Un ejemplo podria ser el siguiente:    
"1:35,4:20"   
"2:25"
"3:"
Los mensajes que empiezan con código "1" contienen un dato de temperatura (35,5 en el ejemplo) y otro de humedad (20), separados por el caracter ':'. Los mensajes que empiezan con código "2" contienen un dato de distancia (25 en el ejemplo). Los mensajes que empiezan por 3 ya no llevan más información e indican que se ha producido un fallo en la captura de datos de temperatura y es necesario activar la alarma correspondiente. A esa lista de tipos de mensajes habrá que ir anadiendo otros nuevos a medida que se vayan necesitando.   

Naturalmente, la estación de tierra que recibirá el mensaje tendrá que usar la función _split_ para trocear el mensaje y determinar el tipo de mensaje recibido a partir del primero de los trozos obtenidos.   

De manera similar es necesario fijar el formato de los mensajes que viajan de la estación de tierra al satélite. Podríamos tener por ejemplo:
"1:5"
"2:90"
"3:"
Los mensajes con código "1" indican el nuevo periodo para enviar datos de temperatura y humedad (5 segundos). Los que tienen el código "2" indican la nueva orientación que debe tomar el sensor de distancia (90 grados en el ejemplo). Los que tienen el código "3" indican que hay que detener el envío de datos de temperatura. Lógicamente, el programa del Arduino satélite debe trocear también los mensajes recibidos para determinar el tipo de mensaje y actuar en consecuencia. El siguiente trozo de código muestra cómo extraer del mensaje recibido la información que contiene.   

```
// la variable comando contiene el string con el mensaje que se acaba de recibir
// vamos a extraer en código que indica el tipo de mensaje
int fin=comando.indexOf(':',0); // fin es la posición que ocupa el primer ':' del mensaje
// Extraigo los caracteres que hay desde el inicio del mensaje hasta la posición fin
// y convierto el resultado en un número entero que es el código
int codigo = comando.substring(0, fin).toInt(); 
int inicio = fin+1;
// ahora segun el código extraigo el resto de la información
if (codigo == 1){
    // cambio del periodo de envio de la temperatura
    // extraigo el valor del nuevo periodo
    fin=comando.indexOf(':',inicio);
    periodoTH = comando.substring(inicio, fin).toInt();
    .....
```
Tomad ya en el equipo las decisiones básicas para vuestro protocolo de aplicación, haciendo una previsión del tipo de mensajes que se van a tener que enviar de un sitio a otro en esta versión 2.

### 5.2 Cálculo de medias de temperatura
Debe incorporarse a las gráficas que se muestran al usuario una que presente la evolución en el tiempo del valor medio de los 10 últimos valores de temperatura. Además, el sistema debe mostrar una alarma al usuario en el caso de que se detecten tres valores medios consecutivos superiores a un valor límite especificado por el usuario.    

El cálculo de esos valores medios puede realizarse en el satélite o en tierra. La ventaja de hacerlo en el satélite es que el sistema puede reaccionar inmediatamente en caso de situación de alarma, por ejemplo, activando un sistema de refrigeración. El inconveniente es que ese cálculo en el satélite consume energía, lo cual no es nada conveniente si el satélite debe estar operativo por un largo periodo de tiempo. El cálculo de los valores medios en tierra tiene justamente las ventajas e inconvenientes contrarios: el gasto de energía para el cálculo es más asumible en tierra pero el sistema no puede reaccionar de manera inmediata a la situación de alarma.   

Se desea, por tanto, que el usuario puede elegir dónde se hace el cálculo de valores medios, si los hace el Arduino satélite (con lo cual esos valores habrá que enviarlos también a tierra) o si los hace la aplicación Python.   

### 5.3 Sensor de distancia
El satélite debe estar dotado de un sistema que permita detectar la proximidad de objetos que puedan impactar con él. Para implementar este sistema usaremos el sensor ultrasónico HC-SR04.    

Este sensor emite un sonido ultrasónico por uno de sus transductores y esperar que el sonido rebote de algún objeto presente. El eco es captado por el segundo transductor. La distancia es proporcional al tiempo que tarda en llegar el eco. Os resultara muy fácil encontrar información sobre cómo conectar el sensor al Arduino satélite y cómo capturar por programa los valores que proporciona.   

Naturalmente el sensor emite el sonido en la dirección en la que está orientado. Para que el sistema sea operativo es necesario que esa orientación pueda cambiar para detectar la proximidad de objetos peligrosos en cualquier dirección. Para conseguir esto montaremos el sensor de ultrasonidos en un servo motor que podemos hacer girar a voluntad por programa. Idealmente, el programa del Arduino satelite hará girar el servo motor de manera constante para conseguir un barrido de toda la zona y captar así la proximidad de objetos en toda la zona barrida. Los datos captados se enviarán a tierra para que puedan mostrarse al usuario.   

La forma ideal para mostrar los datos del sensor de ultrasonidos es una gráfica tipo radar como la que se muestra en la imagen siguiente. 
<img  src="https://github.com/user-attachments/assets/e9d0619a-bab3-4fdc-839a-6ab57e9af99b" width="400" height="300"/>    
Conviene también que desde la estación de tierra se pueda dar la orden al satélite para que oriente el sensor en una dirección concreta en la que se aprecia un mayor peligro.    

Debe incluirse el código necesario para detectar el fallo en el funcionamiento del sensor de distancia y mostrar una alarma en la estación de tierra (quizá un nuevo led de color).   

Finalmente, resultará muy útil tener un nuevo test unitario que nos permita verificar el correcto funcionamiento del sensor de distancia.

### 5.4 Modificación de los periodos de transmisión
Para completar la versión 2 se desea que desde la interfaz gráfica se pueda cambiar el periodo de transmisión de los datos de temperatura/humedad/medidas. También se desea poder parar/reanudar la transmisión los datos de distancia y modificar su periodo de transmisión.   

### 5.5 Entrega de la versión 2   
La lista siguiente es un resumen de lo que debería estar funcionando en la versión 2.
 
1. El controlador capta correctamente los datos de humedad, temperatura y distancia.
2. La estación de tierra recibe correctamente los datos que le envía el controlador y los muestra en gráficas dinámicas apropiadas.
3. Las gráficas dinámicas están incrustadas en la interfaz gráfica.
4. Las gráficas también muestran la evolución del valor medio de las últimas 10 temperaturas.
5. El usuario puede elegir dónde deben calcularse las medias de las 10 últimas temperaturas (si en el satélite o en tierra).
6. El usuario puede parar/reanudar el envío de los datos de humedad/temperatura y el envio de datos de distancia.
7. El usuario puede cambiar el periodo de envío de datos de temperatura/humedad y de distancia.
8. El controlador avisa correctamente a la estación de tierra en el caso de que no pueda captar bien los datos de temperatura/humedad o los datos de distancia (por ejemplo, porque se han desconectado los sensores).
9. La estación de tierra detecta un fallo en la comunicación con el controlador y avisa al usuario de esta circunstancia.
10. El usuario puede poner al sensor de distancia en modo rastreo (hace un barrido continuo de toda la zona alrededor del satelite) y también puede establecer una orientación determinada para el sensor.
11. El usuario puede establecer el valor máximo de temperatura que hará que salte una alarma si se reciben tres valores medios seguidos por encima de ese valor máximo.
12. El usuario de la estación de tierra no tiene ninguna duda de como interactuar con la interfaz gráfica ni para interpretar correctamente la información que se muestra en consola (tanto los datos como las alarmas)
13. El código está bien estructurado e indentado. Es fácil localizar en que parte del código que hace cada una de las operaciones de la versión 1.
14. Se han añadido comentarios clarificadores. En particular, hay comentarios que describen claramente el protocolo de aplicación. Cada función tiene un comentario que describe lo que hace, qué parámetros tiene y qué resultado produce.
15. Se ha implementado correctamente una cola circular para facilitar el cálculo de la media de los últimos 10 valores de temperatura.

La entrega de la versión 2 tiene dos partes. Por una parte debe entregarse un fichero comprimido con los códigos, que debe incluir:   

* El código del Arduino satélite
* El código del Arduino de tierra
* El código de la interfaz gráfica
* En una carpeta adicional: los códigos de los test unitarios que hayais preparado.   

Por otra parte debe entregarse un vídeo de no más de 5 minutos que muestre el correcto funcionamiento de los elementos del sistema que son novedad en la versión 2 (y, por tanto, no se mostraron en el vídeo de la versión 1). También debe mostrar las partes del código implicadas en las nuevas funcionalidades. 

## 6. Versión 3
Las novedades principales de la versión 3 son: un sistema de detección de errores en la comunicación, el envío por parte del satélite de datos sobre su posición que se mostrarán en una gráfica apropiada, la implementación de un sistema de comunicación inalámbrica entre el satélite y la estación de tierra y la implementación de un sistema de registro de eventos.    

### 6.1 Detección de errores en la comunicación
El enlace de comunicación entre el satélite y la estación de tierra puede tener fallos (por ejemplo, bits que se pierden o cambian de valor por el camino). No estamos hablando por tanto de que se haya interrumpido la comunicación (para lo cual ya tenemos un sistema de alarma) sino de un problema de corrupción en el contenido del mensaje. Es necesario incorporar al sistema de algún mecanismo que permita detectar que se ha producido un error y que el mensaje recibido debe ignorarse.   

Un sistema ampliamente usado consiste en añadir al mensaje un checksum. Se trata de un byte que se añade al final del mensaje y que se calcula haciendo la suma de todos los bytes del mensaje y truncando el resultado para que quepa en un byte. El programa transmisor calcula el checksum, lo añade al final del mensaje y lo envía todo.  El programa receptor separa el checksum del mensaje, recalcula el checksum y verifica que coincide con el valor que venía en el mensaje. Si el mensaje ha sufrido alteraciones durante el viaje los valores no van a coincidir y, por tanto, el mensaje debe descartarse. Para probar el correcto funcionamiento de este mecanismo conviere idear alguna manera de alterar el mensaje en el satélite, después de haber calculado su checksum y antes de que el mensaje sea transmitido.       

Implementad en vuestro sistema un mecanismo de checksum que permita descartar los mensajes que han sufrido alteraciones durante la transmisión.   

### 6.2 Posición del satélite    

Hasta ahora hemos aprendido a interactuar con los sensores y actuadores en Arduino, a transmitir información desde el satelite hasta la estanción de tierra y viceversa. Lamentablemente no podemos enviar nuestra Arduino al espacio (todavia) pero si podemos programarla para que simule el movimiento de un satelite en orbita. Para esta primera versión de la simulación, asumiremos que el satelite realiza una orbita circular alrededor de la tierra a una altura constante en el plano ecuatorial.

#### Simulador de movimiento orbital en Arduino

```c
// Constants
const double G = 6.67430e-11;  // Gravitational constant (m^3 kg^-1 s^-2)
const double M = 5.97219e24;   // Mass of Earth (kg)
const double R_EARTH = 6371000;  // Radius of Earth (meters)
const double ALTITUDE = 400000;  // Altitude of satellite above Earth's surface (meters)
const double EARTH_ROTATION_RATE = 7.2921159e-5;  // Earth's rotational rate (radians/second)
const unsigned long MILLIS_BETWEEN_UPDATES = 1000; // Time in milliseconds between each orbit simulation update
const double  TIME_COMPRESSION = 90.0; // Time compression factor (90x)

// Variables
unsigned long nextUpdate; // Time in milliseconds when the next orbit simulation update should occur
double real_orbital_period;  // Real orbital period of the satellite (seconds)
double r;  // Total distance from Earth's center to satellite (meters)

void setup() {
    Serial.begin(9600);
    nextUpdate = MILLIS_BETWEEN_UPDATES;
    
    r = R_EARTH + ALTITUDE;
    real_orbital_period = 2 * PI * sqrt(pow(r, 3) / (G * M));
}

void loop() {
    unsigned long currentTime = millis();
    if(currentTime>nextUpdate) {
        simulate_orbit(currentTime, 0, 0);
        nextUpdate = currentTime + MILLIS_BETWEEN_UPDATES;
    }
    // Other code here
}

void simulate_orbit(unsigned long millis, double inclination, int ecef) {
    double time = (millis / 1000) * TIME_COMPRESSION;  // Real orbital time
    double angle = 2 * PI * (time / real_orbital_period);  // Angle in radians
    double x = r * cos(angle);  // X-coordinate (meters)
    double y = r * sin(angle) * cos(inclination);  // Y-coordinate (meters)
    double z = r * sin(angle) * sin(inclination);  // Z-coordinate (meters)

    if (ecef) {
        double theta = EARTH_ROTATION_RATE * time;
        double x_ecef = x * cos(theta) - y * sin(theta);
        double y_ecef = x * sin(theta) + y * cos(theta);
        x = x_ecef;
        y = y_ecef;
    }

    // Send the data to the serial port
    Serial.print("Time: ");
    Serial.print(time);
    Serial.print(" s | Position: (X: ");
    Serial.print(x);
    Serial.print(" m, Y: ");
    Serial.print(y);
    Serial.print(" m, Z: ");
    Serial.print(z);
    Serial.println(" m)");
}
```

Si observamos el codigo veremos que cada MILLIS_BETWEEN_UPDATES milisegundos se llama a la función simulate_orbit que calcula la posición del satelite en función del tiempo.

La posición se calcula en coordenadas polares y se convierte a coordenadas cartesianas x,y,z. El eje de coordenadas esta posicionado en el centro de la tierra, el eje x apunta hacia el ecuador, el eje y apunta hacia el meridiano de Greenwich y el eje z apunta hacia el polo norte.

Las coordenadas calculadas se envian por el puerto serie para ser visualizadas en el ordenador, segun el formato: Time: 0 s | Position: (X: 6371000 m, Y: 0 m, Z: 400000 m).

Una orbita a 400 km de altura tarda aproximadamente 90 minutos en completarse. Para acelerar la simulación se ha añadido un factor de compresión de tiempo de 90x, con lo cual una orbita completa se simula en poco más de un minuto.

Si cargamos el código en nuestra Arduino y abrimos el monitor serie, veremos las coordenadas que simulan como el satelite se mueve en orbita alrededor de la tierra.

NOTA: Fijaros que para esta versión de la simulación, el satelite se mueve en un plano fijo (la Z siempre es 0) y no se tiene en cuenta la rotación de la tierra.

#### Visualización en Python

Para visualizar la orbita del satelite en Python, podemos utilizar la libreria pyserial para leer los datos enviados por la Arduino y la libreria matplotlib para dibujar un gráfico 3D de la orbita. Para esta primera versión no utilizaremos la comunicación por radio LoRa, sino que conectaremos la Arduino directamente al ordenador mediante un cable USB. Esto es asi para simplificar la comunicación y centrarnos en la visualización de la orbita. Obviamente cuando tengamos esta parte funcionando, podremos añadir la comunicación LoRa.

```python
import sys
import matplotlib.pyplot as plt
import re
import matplotlib

# Use TkAgg backend for interactive plotting
matplotlib.use('TkAgg')

# Regular expression to extract the X, Y, and Z coordinates from the input
regex = re.compile(r"Position: \(X: ([\d\.-]+) m, Y: ([\d\.-]+) m, Z: ([\d\.-]+) m\)")

# Initialize lists to store the X, Y coordinates for plotting
x_vals = []
y_vals = []

# Constants
R_EARTH = 6371000  # Radius of Earth in meters

# Set up the plot
plt.ion()  # Turn on interactive mode for dynamic updates
fig, ax = plt.subplots()
orbit_plot, = ax.plot([], [], 'bo-', label='Satellite Orbit', markersize=2)  # Line for the orbit with smaller markers
last_point_plot = ax.scatter([], [], color='red', s=50, label='Last Point')  # Scatter plot for the last point

# Draw the Earth's surface as a circle
earth_circle = plt.Circle((0, 0), R_EARTH, color='orange', fill=False, label='Earth Surface')
ax.add_artist(earth_circle)

# Set initial plot limits
ax.set_xlim(-7e6, 7e6)
ax.set_ylim(-7e6, 7e6)
ax.set_aspect('equal', 'box')
ax.set_xlabel('X (meters)')
ax.set_ylabel('Y (meters)')
ax.set_title('Satellite Equatorial Orbit (View from North Pole)')
ax.grid(True)
ax.legend()

# Flag to indicate if the window is closed
window_closed = False

# Function to handle window close event
def on_close(event):
    global window_closed
    print("Window closed")
    plt.close(fig)
    window_closed = True
    sys.exit(0)

# Connect the close event to the handler
fig.canvas.mpl_connect('close_event', on_close)

# Function to draw the Earth's slice at a given Z coordinate
def draw_earth_slice(z):
    slice_radius = (R_EARTH**2 - z**2)**0.5 if abs(z) <= R_EARTH else 0
    earth_slice = plt.Circle((0, 0), slice_radius, color='orange', fill=False, linestyle='--', label='Earth Slice at Z')
    return earth_slice

# Initialize the Earth's slice
earth_slice = draw_earth_slice(0)
ax.add_artist(earth_slice)

# Read form serial port in real-time
import serial
ser = serial.Serial('COM4:', 9600, timeout=1)

while not window_closed:
    if ser.in_waiting <= 0:
        continue
    
    line = ser.readline().decode('utf-8').rstrip()

# Read from standard input in real-time
#for line in sys.stdin:
    if window_closed:
        break

    # Search for the line containing the satellite's position
    match = regex.search(line)
    if match:
        x = float(match.group(1))
        y = float(match.group(2))
        z = float(match.group(3))

        print(f"X: {x}, Y: {y}, Z: {z}")

        # Append the new position to the lists
        x_vals.append(x)
        y_vals.append(y)

        # Update the plot
        orbit_plot.set_data(x_vals, y_vals)
        last_point_plot.set_offsets([[x_vals[-1], y_vals[-1]]])  # Update the last point

        # Remove the old Earth's slice and add the new one
        earth_slice.remove()
        earth_slice = draw_earth_slice(z)
        ax.add_artist(earth_slice)

        # Check if the new point is outside the current limits and update limits if necessary
        xlim = ax.get_xlim()
        ylim = ax.get_ylim()
        if abs(x) > max(abs(xlim[0]), abs(xlim[1])) or abs(y) > max(abs(ylim[0]), abs(ylim[1])):
            new_xlim = max(abs(xlim[0]), abs(xlim[1]), abs(x)) * 1.1
            new_ylim = max(abs(ylim[0]), abs(ylim[1]), abs(y)) * 1.1
            ax.set_xlim(-new_xlim, new_xlim)
            ax.set_ylim(-new_ylim, new_ylim)
            # Debugging information
            print(f"Updated plot limits: xlim={ax.get_xlim()}, ylim={ax.get_ylim()}")
    
        plt.draw()
        fig.canvas.flush_events()  # Force a redraw of the plot

# Show the final plot when the input ends
plt.ioff()
plt.show()
```
En este código se lee la salida de la Arduino por el puerto serie y se dibuja la orbita del satelite en un gráfico. El gráfico muestra la orbita del satelite en el plano ecuatorial de la tierra visto desde el polo norte. La tierra se representa como un circulo naranja y la orbita del satelite como una linea azul. El ultimo punto de la orbita se representa como un punto rojo.

Para ejecutar este código necesitamos tener instalado Python y las librerias pyserial y matplotlib. Para instalarlas podemos ejecutar `pip install pyserial matplotlib`.

*IMPORTANTE:* Para que este código funcione, necesitamos tener la Arduino conectada al ordenador mediante un cable USB y que el puerto serie sea el mismo que se ha especificado en el código. Recordad que si tenemos abierto el monitor serie de Arduino, NO podremos acceder al puerto serie desde Python, y el programa fallara. Esto es así que Windows solo permite un programa a la vez acceder al puerto serie. Con ocultar la ventana del monitor serie es suficiente para que Python pueda acceder al puerto serie.



### 6.3 Comunicación inalámbrica
En las versiones anteriores la comunicación entre el Arduino satélite y el Arduino tierra se ha hecho, por comodidad, por cable, usando el protocolo UART de comunicación serie. Pero como es lógico, en el sistema final la comunicación debe realizarse de forma inalambrica. En esta versión 3 vamos a experimentar ya con esta comunicación inalambrica, para lo cual usaremos la tecnología LoRa (Long Range) que está diseñado para comunicaciones a gran distancia y con poco consumo de energía que es justo lo que necesitamos para la comunicación con satélites. En el proyecto usaremos el kit LoRa que usa el chip SX1276 (hay otros modelos cuyo funcionamiento puede ser diferente).   

La comunicación usando LoRa también es una comunicación serie que utiliza el protocolo UART. Los programas de los Arduinos deben crear un canal de comunicación usando la librería _SoftwareSerial_ exactamente igual que hasta ahora. Eso implica que el uso de LoRa no implica ningún cambio en el código de los programas. Eso sí, es necesario incorporar los elementos hardware del kit, que es lo que resumimos a continuación.   

El transmisor/receptor LoRa debe conectarse al Arduino tal y como muestra la figura.    

<img  src="https://github.com/user-attachments/assets/fa49ade5-4acd-49a0-89ca-db71a19a6d10" width="400" height="150"/>   

Como puede observarse, el pin 5 de LoRa (TXD) debe conectarse al pin 10 de Arduino (el RX del canal de comunicación). Por otra parte, el pin 4 de LoRa (RXD) debe conectarse a un divisor de tensión que a su vez se conecta al pin 11 de Arduino (TX del canal de comunicación). Esto se debe a que el chip LoRa trabaja con un voltaje de 3.3V (Arduino trabaja con 5V). Que Arduino reciba por RX la señal de solo 3.3V que le envía LoRa no es problema porque Arduino puede interpretarla bien. Pero que LoRa reciba por RXD una señal de 5V del TX de Arduino puede causar un mal funcionamiento del chip. Por eso, la señal  TX de Arduino (pin 11) se pasa por el divisor de tensión que hace que esos 5V se reduzcan en una tercera parte, de manera que lo que llega a LoRa es aproximandamente esos 3.3V que necesita.   

Conectando los chips LoRa de la forma indicada en ambos Arduinos las comunicaciones deberían funcionar sin problema y sin cambiar nada en el código. No obstante, en el caso de que haya varios sistemas funcionando simultáneamente (por ejemplo, varios grupos probando las comunicaciones inalámbricas al mismo tiempo) pueden producirse interferencias en las comunicaciones, es decir, que la estación de tierra de un grupo reciba los mensajes que envía el satélite de otro grupo. Esto es lógico porque los equipos LoRa de ambos grupos trabajan en el mismo rango de frecuencias. ¿Qué solución puede darse a este problema? Seguro que en clase se discutirán esas posibles soluciones.    
  
 
### 6.4 Registro de eventos
El sistema debe mantener un registro de eventos que pueda ser consultado fácilmente por el usuario. Deben considerarse al menos tres tipos de eventos:   
 
* Comandos que envía la estación de tierra al satélite (por ejemplo, "detener envío de temperatura")   
* Alarmas (por ejemplo, "mensaje corrupto" o "temperatura excesiva")   
* Observaciones del usuario (por ejemplo, "salgo un momento a comer")

Para cada evento queremos tener:   
* Dia/hora en el que se ha producido
* Tipo de evento (uno de los tres anteriores)
* Descripción

Para el caso de los eventos de tipo "Observaciones del usuario" la interfaz gráfica debe tener los elementos necesarios para que el usuario pueda introducir sus observaciones.   
 
Los eventos deben guardarse en un fichero de texto, para que no se pierdan al cerrar la aplicación. Además, la interfaz gráfica debe permitir consultar cómodamente los eventos, filtrandolos por dia/hora y por tipo de evento.    

### 6.5 Entrega de la versión 3   
La lista siguiente es un resumen de lo que debería estar funcionando en la versión 3.
 
1. El controlador capta correctamente los datos de humedad, temperatura, distancia y posición del satélite.
2. La estación de tierra recibe correctamente los datos que le envía el controlador y los muestra en gráficas dinámicas apropiadas (incluida la gráfica 2D con la posición del satélite).
3. Las gráficas dinámicas están incrustadas en la interfaz gráfica.
4. Las gráficas también muestran la evolución del valor medio de las últimas 10 temperaturas.
5. El usuario puede elegir dónde deben calcularse las medias de las 10 últimas temperaturas (si en el satélite o en tierra).
6. El usuario puede parar/reanudar el envío de los datos de humedad/temperatura, el envio de datos de distancia y el envío de la posición del satélite.
7. El usuario puede cambiar el periodo de envío de datos de temperatura/humedad, de distancia y de posición.
8. El controlador avisa correctamente a la estación de tierra en el caso de que no pueda captar bien los datos de temperatura/humedad o los datos de distancia (por ejemplo, porque se han desconectado los sensores).
9. La estación de tierra detecta un fallo en la comunicación con el controlador y avisa al usuario de esta circunstancia.
10. El usuario puede poner al sensor de distancia en modo rastreo (hace un barrido continuo de toda la zona alrededor del satelite) y también puede establecer una orientación determinada para el sensor.
11. El usuario puede establecer el valor máximo de temperatura que hará que salte una alarma si se reciben tres valores medios seguidos por encima de ese valor máximo.
12. El usuario puede introducir en el sistema texto con sus observaciones en cualquier momento.
13. El sistema registra en ficheros los 3 tipos de eventos (alarmas, comandos y observaciones).
14. El usuario puede consultar en cualquier momento los eventos registrados, filtrando por dia y por tipo de evento.
15. El sistema funciona correctamente al sustituir la comunicación por cable por la comunicación inalámbrica.
16. El sistema de comunicaciones usa el mecanismo de checksum para detectar alteraciones en el mensaje.
17. El usuario de la estación de tierra no tiene ninguna duda de como interactuar con la interfaz gráfica ni para interpretar correctamente la información que se muestra en consola (tanto los datos como las alarmas)
18. El código está bien estructurado e indentado. Es fácil localizar en que parte del código que hace cada una de las operaciones de la versión 1.
19. Se han añadido comentarios clarificadores. En particular, hay comentarios que describen claramente el protocolo de aplicación. Cada función tiene un comentario que describe lo que hace, qué parámetros tiene y qué resultado produce.
20. Se ha implementado correctamente una cola circular para facilitar el cálculo de la media de los últimos 10 valores de temperatura.

Como en los casos anteriores, la entrega de la versión 3 tiene dos partes. Por una parte debe entregarse un fichero comprimido con los códigos, que debe incluir:   

* El código del Arduino satélite
* El código del Arduino de tierra
* El código de la interfaz gráfica
* En una carpeta adicional: los códigos de los test unitarios que hayais preparado.   

Por otra parte debe entregarse un vídeo de no más de 5 minutos que muestre el correcto funcionamiento de los elementos del sistema que son novedad en la versión 3 (y, por tanto, no se mostraron en el vídeo de la versión 2). También debe mostrar las partes del código implicadas en las nuevas funcionalidades. 


## 7. Versión 4 (final)
La versión 4 no tiene requisitos específicos. Naturalmente, es una ultima oportunidad para incorporar los requisitos previstos en las versiones anteriores y que aún no están operativos. No obstante, lo importante de la versión final es que se abre la puerta a funcionalidades adicionales ambiciosas que puedan sorprender a vuestros profesores. Recordad que una parte de la calificación del proyecto depende de esas funcionalidade adicionales.   

Es muy probable que el grupo ya tenga ideas para mejorar el sistema. En todo caso, aquí se proponen tres retos ambiciosos. Quizá alguno de ellos capte vuestra atención.    
### 7.1 Comunicaciones más ligeras
Una manera de mejorar la eficiencia de nuestro sistema de comunicación entre satélite y estación de tierra es compactar la información que se envía. Si tenemos un mensaje que ocupa 10 bytes (80 bits) y podemos compactar la misma información en solo 2 bytes entonces conseguiremos que el enlace de comunicación esté menos saturado, lo cual permitirá, por ejemplo, aumentar la frecuencia de envío de datos del satélite a tierra.   
 
Veamos un ejemplo. Supongamos que tenemos que enviar un mensaje que contiene 4 datos:    
* El código (un número entre 0 y 3)   
* El dato A (un número entre 0 y 7)   
* El dato B (un número entre 0 y 7)   
* El dato C (un número entre 0 y 31)   
* El dato D (un número entre 0 y 7)   
  
Esta información podría enviarse en forma de cadena de caracteres: “2/3/5/22/6”. Esta cadena ocupa 10 bytes, que son los que se necesitan para codificar en ASCII cada uno de los 10 caracteres de la cadena. Sin embargo, atendiendo al tamaño que pueden tener cada uno de los 4 datos, podríamos codificar el mensaje en 2 bytes, tal y como muestra la figura.   
    
 <img  src="https://github.com/user-attachments/assets/8f018e20-0158-4dd6-bfce-535b40f8d015" width="400" height="100"/>    
  
Puesto que el código se puede codificar con 2 bits, los valores de A, B y D se pueden codificar con 3 bits y el valor de C se puede codificar con 5 bits, un total de 16 bits (2 bytes) son suficientes para codificar el mensaje completo, frente a los 10 bytes del mensaje en forma de cadena e caracteres.    
 
Para poder hacer las operaciones de compactación y des-compactación de los mensajes es necesario aprender a trabajar a nivel de bit (máscaras, desplazamientos, AND y OR). Veamos lo esencial sobre esta cuestión.    
```
uint8_t RES = (DATO1 << 2) | DATO2;
```
Suponiendo que en DATO1 hay un número del 0 al 63 que, por tanto, puede codificarse con 6 bits, y en DATO2 hay un número del 0 al 3 (que se codifica con 2 bits) la sentencia anterior desplaza dos posiciones hacia la izquierda los bits del DATO1 para hacer sitio al DATO2 y luego hace la operación OR bit a bit (|), con lo cual se inyecta el valor de DATO2 en los dos bits bajos del resultado, que se almacena en una variable de tipo unit8_t, que contiene un entero sin signo de 8 bits. Si DATO1 contiene el número 13 y DATO2 el número 2, el contenido de RES será (en binario) *001101***10** (en itálica los bits que codifican el DATO1 y en negrita los que codifican el DATO2). Para comprender bien esta sentencia hay que entender que la operación OR entre dos bits da 0 si ambos bits son 0 y da 1 si al menos uno de los dos bits es 1.   

```
int DATO1 = (RES & 0b11111100) >> 2;
int DATO2 = (RES & 0b00000011);
```
Estas dos sentencias permiten extraer los valores de DATO1 y DATO2 aplicando sobre RES máscaras binarias, la operación AND (&) bit a bit y un desplazamiento de 2 bits a la derecha. Al aplicar la operación AND a dos bit el resultado es 0 si al menos uno de los dos bits es 0 y da 1 si ambos bits son 1.   
 
Este es un ejemplo más que incluye las operaciones de envío y recepción del mensaje a través del puerto serie.
transmisor.
```
// enviar un mensaje con 
// los 5 datos siguientes
int cod = 3; // número entre 0 y 3
int A = 2; // número entre 0 y 7
int B = 5; // numero entre 0 y 7
int C = 22; // número entre 0 y 31
int D = 6; // número entre 0 y 7

// necesito 2 bytes para 
// empaquetar el mensaje
uint8_t buffer[2]; 
    
// en el primer byte caben cod, A y B
buffer[0] = (cod << 6) | (A << 3) | B;  
// en el segundo byte caben C y D
buffer[1] = (C << 3) | D;
// transmitimos
miSerial.write (buffer,2);	receptor

// necesito 2 bytes para 
// recibir el mensaje
uint8_t buffer[2];

// leemos los 2 bytes
miSerial.readBytes(buffer, 2);

// extraigo el codigo del primer byte
int cod = ((buffer[0] & 0b11000000) >> 6);  
// extraigo A
int A = (buffer[0] & 0b00111000) >> 3;
// extraigo B
int B = (buffer[0] & 0b00000111);
// extraigo C del segundo byte
int C = (buffer[1] & 0b11111000) >> 3;
// extraigo D
int D = (buffer[1] & 0b00000111);
```

El ejemplo muestra que para transmitir el mensaje compactado debe usarse la función *miSerial.write*, que envía los datos en crudo (en binario). Si se usase *miSerial.println* se convertiría el contenido del buffer es una cadena de códigos ASCII correspondientes a los números contenidos, con lo que perderíamos todo lo ganado con la operación.    
 
El reto consiste, por tanto, en introducir el código necesario para compactar y des-compactar mensajes, y verificar que ese cambio permite aumentar significativamente la frecuencia de las comunicaciones sin saturar el enlace inalámbrico entre el satélite y la estación de tierra.

### 7.2 Comunicaciones más seguras
Las comunicaciones entre vuestro satélite y la estación de tierra no son seguras. Ya hemos visto que los mensajes que envía el satélite pueden ser recibidos e interpretados correctamente por la estación de tierra del resto de grupos de clase. Puede que eso no represente un problema. Si los datos que envía el satélite no son confidenciales (por ejemplo, datos que se harán públicos en cuanto los reciba la estación de tierra para que los científicos de todo el mundo se beneficien) entonces no importa mucho que un satélite espía averigüe esos datos un poco antes que el resto del mundo. Pero incluso en ese caso en el que la confidencialidad no es necesaria, podemos tener un problema de autentificación. Nada impediría a un satélite espía enviar un mensaje haciéndose pasar por otro, con el objetivo de enviar información falsa (un nuevo bulo).   
 
Sería conveniente, por tanto, dotar a vuestro sistema de mecanismos que implementen comunicaciones más seguras. Veamos cómo hacerlo. La cosa empieza con la triste historia de María y Juan.   
 
<ins>La triste historia de Juan y María  </ins>     

Juan está desesperado. Necesita urgentemente 1000 euros por un asunto del que prefiere no dar explicaciones a nadie. Decide pedirle ese dinero a su amiga María. Le va a proponer que le lleve el dinero en metálico el martes a las 12 de la noche a un punto discreto de la ciudad.   
 
Le prepara una carta con esas instrucciones, pero justo cuando va a enviársela piensa que es un método peligroso porque alguien puede interceptar la carta y preparar una emboscada a María para robarle el dinero. Entonces la llama por teléfono para explicarle sus dudas y ella le dice: “!Pues dime las instrucciones por teléfono ahora!”. Pero él le contesta: “No, que con el rollo ese del programa Pegasus no me fio. Igual me están espiando el móvil”.   
 
María es una tía muy lista y tiene una idea.  Compra un candado y lo lleva a Correos. Allí les da las siguientes instrucciones. “Pongan mi nombre en este candado y entréguenselo abierto a la persona que venga a recogerlo. Yo me llevo a casa la llave del candado. De esta manera, la persona que recoja el candado podrá enviarme en una caja cerrada lo que quiera, con la seguridad de que solo yo podré abrir la caja”. En Correos aceptan y se quedan con el candado abierto a la espera de que alguien venga a reclamarlo.   
 
María llama a Juan para explicarle su idea. Pero Juan también es listo y le dice lo siguiente: “Para que tu idea funcione yo debo estar absolutamente seguro de que el candado que me den en correos es tuyo y no de cualquier otra persona que se haga pasar por ti. De hecho, si el puto programa Pegasus está en mi móvil ahora mismo alguien nos estará escuchando y mañana irá a correos a dejar un candado haciéndose pasar por ti. Yo recogeré el candado, te enviaré el mensaje, pero ellos interceptarán la caja y la abrirán con la llave de ese candado”.   
 
María comprende el problema y va a Correos para explicarlo. Allí le proponen una solución: “Nosotros podemos verificar que tú eres realmente Maria y poner tu nombre en tu candado. Eso sí, tu amigo debe fiarse de nosotros. Confiar en que hemos hecho una buena verificación”. A Maria le parece buena idea, saca sus documentos de identidad para que Correos pueda verificar que ella es realmente Maria. Cuando están a punto de acabar, el personal de Correos comprende que lo que está haciendo puede ser un servicio de futuro y decide cobrarle a Maria 100 euros por ese servicio de acreditación. Maria no tiene más remedio que aceptar.      
 
María llama a Juan y le explica la nueva situación. Ahora Juan puede ir a correos a buscar el candado con la seguridad de que le van a dar el candado abierto de María, que, una vez cerrado, solo ella puede abrir. Pero, un segundo antes de colgar, María reacciona y dice: “Un momento. Si alguien acaba de escuchar nuestra conversación con el puto Pegasus de los cojones, puede que vaya a correos a pedir mi candado y enviarme un mensaje con instrucciones para hacerme una emboscada. Este sistema no es seguro”.     
 
Entonces Juan tiene otra idea. Va a Correos y les lleva otro candado. Les propone que ellos se queden con la llave de ese candado y que se la den a quien venga a buscarla. Él se llevará su candado abierto. Además, les enseña sus documentos de identidad para acreditar que él es realmente Juan. Entonces les dice: “Deme el candado de María”. Mete el sobre con las instrucciones en una caja y la cierra con el candado de María. Además, le pone su propio candado y deja en Correos la caja cerrada con los dos candados.     
 
Cuando llega a casa, Juan llama a María y le explica lo siguiente: “Ve a Correos y pídeles la caja que he dejado para ti. Pídeles también mi llave. Ellos te pueden asegurar que esa llave es mía y de nadie más. Allí mismo trata de abrir el candado que lleva mi nombre. Si consigues abrirlo puedes estar segura de que esa caja la he dejado yo porque en Correos te asegurarán que la llave que te han dejado es mía y de nadie más (ya pagué yo también los 100 euros para que se asegurasen de eso). Cuando llegues a tu casa abre el candado que lleva tu nombre con tu llave. Yo estoy seguro de que ese candado es tuyo y solo lo puedes abrir tú, porque así me lo han asegurado en Correos.  
 
Convencidos de que el método ahora sí que seguro, Juan y Maria llevaron a cabo el plan. María se presentó con los 1000 euros en el lugar y la hora indicados en la carta, pero Juan no apareció. Resultó que habían tardado mucho tiempo en idear el sistema seguro. La mafia no esperó más y le cortó el cuello a Juan. Eso sí, desde aquel día, Correos se está forrando con el dinero que gana con ese nuevo servicio de comunicación segura inventado por Maria y Juan.   

<ins>La esencia de la comunicación segura  </ins>     
 
La historia de Juan y María ilustra los conceptos básicos en los que se fundamentan los modelos de comunicación segura usados hoy en día. El sistema tiene que garantizar dos cosas:      

* Confidencialidad: el mensaje que envía Juan solo puede leerlo Maria (o viceversa)   
* Autentificación: el mensaje que recibe Juan solo puede haber sido enviado por Maria (o viceversa)
  
Para ello, cada implicado en la comunicación necesita una clave pública y una privada. Para Juan la clave pública es la llave de su candado. La deja en Correos y puede cogerla cualquiera. Pero la clave privada es el candado, que solo tiene él. Para María la cosa va al revés. Su clave pública es el candado que deja a su nombre en Correos y está disponible para cualquier. Su clave privada es la llave que guarda en casa.    
 
Para garantizar autentificación, Juan cierra el mensaje con su candado y cualquiera puede abrirlo con su llave, que es pública, asegurándose de esta manera que el candado solo puede haberlo cerrado Juan.    
 
Para garantizar confidencialidad, Juan cierra el mensaje con el candado público de Maria, con la tranquilidad de que solo ella puede abrirlo con la llave privada que tiene en casa.     
 
Pero para que todo esto funcione se necesita una autoridad respetada por los implicados (en este caso, Correos) que certifique que la persona que deja en Correos su candado es realmente Maria y la que deja su llave es Juan.     
  
Un sistema así es el que necesitamos para garantizar comunicaciones seguras entre el satélite y la estación de tierra. Pero claro, los ordenadores no trabajan con candados y llaves. Trabajan con números. ¿Es posible hacer algo así con números? Pues resulta que sí. Que solo necesitamos tres números.     

<ins>El algoritmo RSA   </ins>          
Tomemos los tres números siguientes: N = 77, E = 7 y D = 43. Supongamos que Juan quiere enviar a María por email un número secreto (por ejemplo, la contraseña de su caja fuerte). Pongamos que ese número es el 68, aunque la cosa va a funcionar con cualquier número menor que N. María envía a Juan los números N y E. Esa pareja de números constituye la clave pública de María. No importa que otras personas se enteren de esa pareja de números. Pero María guarda en secreto el número D (que es su clave privada).   

Para encriptar el número secreto, Juan hace la operación siguiente:      
68<sup>E</sup> módulo N   

El resultado de eso es 40, que es el número que envía a María. Cuando María recibe el número hace la operación siguiente:       
40<sup>D</sup> módulo N   
 
Y obtiene como resultado el 68, la contraseña de la caja fuerte.  Obviamente eso no funciona con cualquier trio de números, pero si con otras combinaciones. Por ejemplo, puedes probar con estas:   

N = 77, E = 7 y D = 43         
N = 77, E = 13 y D = 37         
N = 77, E = 23 y D = 47  
 
Todas esas combinaciones permiten encriptar/desencriptar números menores de 77.   

La siguiente combinación permite encriptar/desencriptar números menores de 143:    

N = 143, E = 23 y D = 47    

De hecho, hay infinidad de combinaciones de números que pueden usarse de esta forma. ¿Dónde está el truco de esta magia?     
  
Esta magia se debe a Rivest, Shamir y Adleman que en 1979 inventaron el algoritmo RSA (las iniciales de sus nombres) para generar números como los anteriores que puedan usarse como claves públicas y privadas. El algoritmo RSA no es muy complicado. Todo parte de dos números primos (por ejemplo, el 7 y el 11 para los ejemplos con N=77 o 11 y 13 para los ejemplos con N = 143). Luego, haciendo unas cuántas operaciones sencillas con esos números se pueden obtener varias combinaciones (N,E,D). Busca en internet información sobre el RSA y no te costará mucho encontrar esas operaciones y hacer un programa que te pida dos números primos y genere todas las combinaciones posibles de (N,E,D) asociadas a esos dos primos.    
 
Naturalmente, el método tal y como se ha descrito aquí no parece muy seguro. Si alguien intercepta la clave pública de María y el número secreto encriptado, puede intentar desencriptarlo probando la fórmula de desencriptación con todos los valores posibles de D (en el ejemplo, los números del 1 al 77). Un sencillo programa podría generar todas las posibilidades hasta encontrar un resultado que tenga sentido.      

Pero claro, la cosa se complica si los dos números primos elegidos son muy muy grandes (por ejemplo, con unos 300 dígitos cada uno). En ese caso, ni las computadoras más potentes pueden realizar esa exploración en un tiempo razonable. Y lo cierto es que hay mucha gente investigando en cómo obtener números primos muy grandes, precisamente para hacer más seguros los sistemas de encriptación (el record actual es un número primo que tiene 23 millones de dígitos, descubierto en 2016).   
  
Para encriptar números pueden usarse exactamente las fórmulas que se han explicado antes. Para encriptar cadenas de texto la cosa es un poco más elaborada. Se encripta por separado cada uno de los caracteres. Para ello se convierte cada carácter en un número del 32 al 126, que son los valores del código ASCII expresados en decimal correspondientes a los caracteres imprimibles (los que pueden aparecer en el mensaje) Luego se encripta el número y se obtiene el carácter imprimible correspondiente al número resultante. La frase con los caracteres resultantes es la que se envía y se desencripta en el destino con el mismo procedimiento. Para que esto funcione tienes que buscar combinaciones en las que la N sea mayor a 126.         


<ins>¿Te animas a hacer más seguro vuestro sistema satelital?</ins>              
No te va a resultar difícil porque en vuestro sistema los mensajes que intercambian el satélite y la estación de tierra son cadenas de texto. Tanto el satélite como la estación de tierra deben generar sus propios juegos de claves pública y privada, e intercambiarse las claves públicas. Con lo descrito en los apartados anteriores (y con un poco de investigación para encontrar esas fórmulas necesarias para implementar el programa que genere claves) ya pueden encriptar y desencriptar los mensajes que se intercambian, con garantías de autenticidad y confidencialidad.   
  
Solo hay un punto que ha quedado en el aire. ¿Cómo está segura, por ejemplo, la estación de tierra, de que la clave pública que le han dado es realmente de su satélite y no de un satélite espía? En otras palabras, ¿dónde está la autoridad certificadora en este caso (la que haga el papel que hizo Correos en el caso de la historia de Juan y Maria)? En este caso, la autoridad certificadora podría ser los profesores de la asignatura. Ellos serían los que proporcionarían los juegos de claves públicas y privadas, asegurándose de que entregan esas claves a las personas que son quienes dicen que son. Naturalmente, a los profesores les costaría medio segundo hacer ese programa para generar las claves. No obstante, vamos a obviar ese paso, porque vuestros profesores están muy ocupados revisando las entregas del curso. A menos que estéis dispuestos a pagarles 100 euros por ese servicio, como hicieron María y Juan con Correos. En ese caso, quizá vuestros profesores estén dispuestos a hablar del tema.

### 7.3 Graficos de posición más realistas
ESTA POR HACER

### 7.4 Calificación    
La versión final si que tiene una calificación (la misma para todos los miembros del equipo) que se determinará a partir de los criterios siguientes:    
   
| Criterio  | Descripción | Peso |
| ------------- | -------------  | ------------- |
| Correcto |El prototipo realiza correctamente todas las funciones especificadas en los requisitos de la versión 3  |40% 
| Robusto |El sistema resiste sin bloquearse los fallos que puedan producirse (por ejemplo, errores del usuario al interactuar con el sistema o fallos en los sensores del satélite) |7.5% |
| Amigable |El usuario no tiene dudas al interactuar con el sistema a través de la interfaz gráfica, que es, además, visualmente agradable.  |7.5% |
| Organizado y documentado	 |El código del controlador y de la estación de tierra está bien organizado en funciones. Además, se han añadido comentarios adecuados que deben permitir a otras personas, con poco esfuerzo, entender el código y hacer modificaciones si son necesarias	  |10% |
| Eficiente |El código usa siempre los algoritmos más adecuados para realizar las operaciones  |5% |
| Sorprendente |Las funcionalidades adicionales son interesantes, complejas y sorprendentes.	  |20% |
| Bien presentado	 |El vídeo que acompaña a la versión final presenta claramente el funcionamiento del sistema y resulta espectacular  |10% |
| TOTAL |  |100% |

