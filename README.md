Este proyecto controla un cohete usando varios sensores y módulos. Se encarga de monitorizar la altitud, la posición GPS, y de desplegar el paracaídas en el momento adecuado. Aquí te explico cómo conectar los componentes y cómo funciona el código.

Componentes Utilizados

Arduino Nano: Es la placa controladora principal del sistema.

Módulo GPS NEO-7: Proporciona la ubicación GPS, altitud, y otros datos relevantes durante el vuelo.

Módulo HC-12: Permite la comunicación inalámbrica con el cohete para enviar datos en tiempo real.

Microservo SG90: Utilizado para el despliegue del paracaídas durante el vuelo.

Sensor Barométrico BMP180: Mide la altitud del cohete con mayor precisión que el GPS.

Conexiones de Hardware

Arduino Nano

Alimentar el Arduino con 5V y GND.

GPS NEO-7

TX (GPS) → Pin 0 (RX) del Arduino

RX (GPS) → Pin 1 (TX) del Arduino

Alimentar con 5V y GND.

Módulo HC-12

Pin 5 del Arduino → RX (HC-12)

Pin 4 del Arduino → TX (HC-12)

Alimentar con 5V y GND.

Microservo SG90

Señal del Servo → Pin 6 del Arduino

Alimentar con 5V y GND.

Sensor Barométrico BMP180

SCL → Pin A5 del Arduino (SCL)

SDA → Pin A4 del Arduino (SDA)

Alimentar con 3.3V y GND.

Descripción del Código

Bibliotecas Utilizadas

SoftwareSerial.h: Para comunicar el Arduino con el módulo HC-12.

Servo.h: Controla el servo que despliega el paracaídas.

Wire.h y Adafruit_BMP085.h: Para obtener datos del sensor barométrico BMP180.

TinyGPS++.h: Gestiona la lectura de datos del módulo GPS.

Variables Principales

Datos del GPS: Se capturan latitud, longitud, altitud, velocidad, y número de satélites.

Variables de Vuelo: Manejan la detección de despegue, ascenso, descenso, y aterrizaje.

Lógica de Vuelo

Despegue: Detecta cuando el cohete ha despegado basándose en la altitud.

Despliegue del Paracaídas: El paracaídas se despliega automáticamente 7 segundos después de detectar el despegue. 

IMPORTANTE: Modifica los segundos dependiendo de cuanto tarde tu cohete en llegar al apogeo.

Aterrizaje: Se determina cuando la altitud es baja y la velocidad vertical se aproxima a cero.

Uso del Servo

El servo se adjunta justo antes del despliegue del paracaídas y se mueve 50 grados para liberar el mecanismo. Luego, regresa a la posición inicial y se desadjunta para ahorrar energía.

Comunicación Inalámbrica

Utiliza el HC-12 para transmitir datos en tiempo real, como altitud, coordenadas GPS y estado del cohete.

Sistema de Recuperación

Se realizan pruebas del sistema de recuperación antes del vuelo para verificar el funcionamiento del GPS, barómetro y servo.

Configuración y Pruebas

Configuración Inicial: Antes de realizar el lanzamiento, el sistema se inicializa y espera a que el GPS obtenga una conexión fija.

Confirmación del Usuario: El sistema solicita varias confirmaciones al usuario para realizar las pruebas y proceder al lanzamiento. Se confirma enviando "1" en valor ASCI.

Pruebas del GPS y Barómetro: Se realizan pruebas para verificar la precisión de los datos y asegurar que los sensores funcionan correctamente.

Cuenta Atrás y Lanzamiento: Una vez completadas las pruebas, se realiza una cuenta atrás de 1 minuto antes de encender el motor. (Por ahora, el motor se enciende manualmente)

Este código es para el arduino NANO que va dentro del cohete. Necesitarás también un arduino con modulo de radiofracuencia recibiendo y transmitiendo.
