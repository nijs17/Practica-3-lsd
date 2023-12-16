# Practica-3-lsd
## INTRODUCCION
### DESCRIPCION 
La **Esp32** la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (**DTH11**) para adquirir temperatura y humedad del entorno; Cabe aclarar que esta practica se usara un simulador llamado WOKWI.
### MATERIAL A OCUPAR
Para realizar esta practica ocuparemos lo siguente:
-WORKI

-Tarjeta ESP 32

-Sensor DHT11

### Requisitos previos
Para poder usar este repositorio necesitas entrar a la plataforma WOKWI.
## INSTRUCIOES DE ELAVORACION 
1.Abrir la terminal de programación y colocar la siguente programación:
 
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
  
}

2. Instalar la libreria de DHT sensor library for ESPx como se muestra en la siguente imagen.
![](https://github.com/nijs17/Practica-2-sensor-DHT22/blob/main/LIB.png)
3. Hacer la conexion de **DHT11** con la **ESP32** como se muestra en la siguente imagen.
![](https://github.com/nijs17/Practica-3-lsd/blob/main/3c.png)

## INSTRUCCIONES DE OPERACION 

    1. Iniciar simulador.
    2. Visualizar los datos en el monitor serial.
    3. Colocar la temperatura y humedad dando doble click al sensor DHT11
## RESUSLTADOS
Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.
![](https://github.com/nijs17/Practica-3-lsd/blob/main/3val.png)
