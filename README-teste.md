# ProjetosIOT
 PProjetos IOT
#include"DHTesp.h"
#include <WiFi.h>
#include<HTTPClient.h>
#define DHT 12
int i = 0;
DHTesp sensor; 

HTTPClient http;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
  Serial.println("Hello, ESP32!");
  pinMode(19, OUTPUT);
  pinMode(18, OUTPUT);
  pinMode(DHT, INPUT);
  pinMode(T2, OUTPUT);
  sensor.setup(DHT, DHTesp::DHT22 );

  Serial.println("Conectando-se ao WiFi");
  WiFi.begin("Wokwi-GUEST", "", 6);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.println("Conectando-se ao WiFi...");
  }
  Serial.println(" Conectado!");

}

void loop() {
delay(3000); 
 float temperatura = sensor.getTemperature();
 delay(3000);
 float humidade = sensor.getHumidity();
 Serial.println(temperatura);
 Serial.println(humidade);
 if(temperatura > 35){
  digitalWrite(19, HIGH);
}else { digitalWrite(19, LOW);}


if(humidade > 50){
  digitalWrite(18, HIGH);
  }else {
    digitalWrite(18, LOW);
  }}

