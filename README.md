# Practica 1_ ESP32 con DTH22 + LCD

**Sensor de Temperatura y Humedad utilizando una LCD**

En esta práctica podemos programar una ESP32 con el sensor DHT22, con visualización en datos en LCD.

## Contenido 

- Introducción 
- Objetivo
- Material Requerido
- Procedimiento 
- Instrucciones de operación 
- Resultados 



## 1. Introducción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```).
### 1.1 Descripción
 El ```DHT22``` utiliza un solo cable digital para la comunicación de datos, lo que hace que su conexión sea sencilla y fácil de implementar en proyectos de electrónica. Este sensor proporciona mediciones de temperatura y humedad de alta precisión, con una precisión de +/-0.5 °C para la temperatura y +/-2-5% para la humedad para adquirir temperatura y humedad del entorno. 
 
 ### 1.2 Especificación 
 Es importante considerar que esta practica se estara realiando en un simulador llamado [WOKWI](https://https://wokwi.com/).

## 2. Objetivo 

Poder diseñar un diagrama con sensor DHT22 de temperatura y humedad que se utilice para medir la temperatura y la humedad relativa del ambiente en el que se encuentra, mediante la utilización de una ESP32.


## 3. Material Requerido

Tomar en cuenta el material necesario para realizar esta práctica:

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
- LCD 16x2 (I2C)



## 4. Procedimiento a realizar 

 - Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


## Paso 1 

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  
 lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");
  delay(1000);

lcd.setCursor(0, 0);
  lcd.print("Practica2 DTH22_LCD      " );
  lcd.setCursor(0, 1);
  lcd.print(" Dulce M RZ              " );

  delay(1000);

}

```


## Paso 2 

2. Instalar la libreria de **DHT sensor library for ESPx** como se muestra en la siguente imagen.

![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/ESP32%20CON%20DHT22%20Y%20LCD%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2010_06_2023%2007_51_57%20a.%20m..png?raw=true)

## Paso 3

3. Hacer la conexion de **DHT22** con la **ESP32** como se muestra en la siguentes imagenes:

3.1 Es importante considerar que para **ESP32** se maneja un ```Voltaje de trabajo 3.3 VDC```. 

a) Observar conexión de pin del Sensor al **pin 1** de **ESP32**. 

![](https://github.com/DulceMRZ/PRACTICA_1_DHT22/blob/main/Practica_1_DTH22%20diagrama%20(1).PNG?raw=true)

b) Conexión de pin 2 (GND) 


![](https://github.com/DulceMRZ/PRACTICA_1_DHT22/blob/main/Practica_1_DTH22%20diagrama%20(2)..PNG?raw=true)

c) Conexión pin 3 (pin 15) 


![](https://github.com/DulceMRZ/PRACTICA_1_DHT22/blob/main/Practica_1_DTH22%20diagrama..png?raw=true)

d) Conexión de LCD 


![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/Captura3.PNG?raw=truee)



e) Conexión de LCD más ESP32 y DHT22

![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/Captura1.PNG?raw=true)



### 5. Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT22** 

## 6. Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.

![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/ESP32%20CON%20DHT22%20Y%20LCD%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2010_06_2023%2007_32_34%20a.%20m..png?raw=true)

![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/ESP32%20CON%20DHT22%20Y%20LCD%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2010_06_2023%2007_32_34%20a.%20m..png?raw=true)

# Créditos

Desarrollado por Dulce M Rodriguez Zarate 

- [GitHub](https://github.com/DulceMRZ)