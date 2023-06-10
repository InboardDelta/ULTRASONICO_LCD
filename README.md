# PRACTICA ESP32 CON ULTRASONICO Y LCD
Este repositorio muestra como podemos programar una **HC-SR04 Ultrasonic Distance Sensor** con el sensor ultrasonico y un **LCD** el cual programaremos con los valores pedidos por el docente.
## MATERIAL NECESARIO

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor **HC-SR04 Ultrasonic Distance Sensor**
- Pantalla LCD **16x2 I2C**
## INTRODUCCION
### DESCRIPCION
La (```Esp32```) la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04 Ultrasonic Distance Sensor```) para obtener el valor de distancia; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/). 
### INSTRUCCIONES
1. Abrir la terminal de programación y colocar la siguente programación:

```
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4
const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 15;   //Pin digital 3 para el Echo del sensor
const int DHT_PIN = 15;
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);
void setup() {
  Serial.begin(9600);//iniciailzamos la comunicación
  lcd.init();
  lcd.backlight();
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
}

void loop()
{

  long t; //timepo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(1000);          //Hacemos una pausa de 100ms
  lcd.setCursor(0, 0);
  lcd.print(" Distancia: " + String(d) +"cm");
  lcd.setCursor(0, 1);
  lcd.print(" Rodrigo Vega");
  delay(1000);
}

```
2.- Se buscaran las herramientas necesarias en el programa como : **HC-SR04 Ultrasonic Distance Sensor** y **LCD 16x2 (I2C)** como se muestra en la imagen.
![](https://github.com/InboardDelta/ULTRASONICO_LCD/blob/main/componentes.png?raw=true)

3.- Realizaremos las conexiones de el sensor **HC-SR04 Ultrasonic Distance Sensor** y la pantalla **LCD 16x2 (I2C)** como se muestra en la imagen.
![](https://github.com/InboardDelta/ULTRASONICO_LCD/blob/main/conexiones.png?raw=true)
4. Instalaremos la libreria de **LiquidCrystal I2C** como se muestra en la siguente imagen.
![](https://github.com/InboardDelta/ULTRASONICO_LCD/blob/main/libreria.png?raw=true)

## RESULTADOS
Cuando haya funcionado, verás los valores dentro del monitor serial considerando que tendremos los valores de distancia y adicionalmente para ocupar la segunda linea de la pantalla LCD se agrega un mensaje predeterminaod por el alumno.
![](https://github.com/InboardDelta/ULTRASONICO_LCD/blob/main/funciona.png?raw=true)
# Comentarios del alumno
Esta practica nos mostro la programación, conexión y funcionamiento de un sensor en conjunto con una pantalla LCD para obtener un valor del sensor y mostrarlo en la pantalla e igualmente poder imprimir en la pantalla un texto predeterminado por el alumno.

# Créditos

Desarrollado por RODRIGO VEGA
- [GitHub](https://github.com/InboardDelta)