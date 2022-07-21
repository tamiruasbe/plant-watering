# plant-watering#include<liquidCrystal.h>
#include<SoftwareSerial.h>
#define echo 9
#define trigger 10
#define tank_pump 4
#define watering_pump 13
#define moisture_sensor A0
long duration;
int distance;
int moisture_value;
int distance_percent;
int moist_percent;
Software Serial SIM900(2,3);
liquidCrystal lcd(12,11,8,7,6,5);
void setup(){
Lcd begin(20,4);
SIM900.begin(9600);
Serial.begin(9600);
pinMode(echo,INPUT);
pinMode(moisture_sensor,INPUT);
pinMode(trigger,OUTPUT);
digitalWrite(trigger,LOW);
pinMode(watering_pump,OUTPUT);
pinMode(tank_pump,OUTPUT);
digitalWrite(watering_pump,LOW);
digitalwrite(tank_pump,LOW);
lcd.setCursor(0,1);
lcd.print("PLant watering using");
lcd.setCursor(0,2);
lcd.print("Moisture Sensor and");
lcd.setCursor(0,3);
lcd.print("Ultrasonic sensor");
delay(500);
lcd(clear);
}
void loop(){
digitalWrite(trigger,LOW);
delayMicroseconds(2);
digitalWrite(trigger,HIGH);
delayMicroseconds(10);
digitalWrite(trigger,LOW);
duration=pulseIN(echo,HIGH);
distance=duration*0.017;
distance_percent=map(distance,0,1023,0,100);
moisture_value=analogRead(moisture_sensor);
moist_percent=map(moisture_value,0,1023,0,100);
condition();}
void sms(){
SIM900.print("to=1\r");
SIM900.println("to=\+215********\");
SIM900.println("Water pump is off");
SIM900.println((char)26);
SIM900.println();}
void sms1(){
SIM900.print("to=1\r");
SIM900.println("to=\+2519********\");
SIM900.println("Tank pump is off");
Serial.println("Tank pump is off");
SIM900.println((char)26);
Serial.println((char)26);
SIM900.println();}
void sms2(){
SIM900.print("to=1\r");
SIM900.println("to=\+2519********\");
SIM900.println("Watering pump is on");
Serial.println("Watering pump is on");
SIM900.println((char)26);
Serial.println((char)26);
SIM900.println();}
void sms3(){
SIM900.print("to=1\r");
delay(500);
SIM900.println("to=\+2519********\");
SIM900.println("Tank pump is on");
Serial.print("Tank pump is on");
SIM900.println((char)26);
Serial.println((char)26);
SIM900.println();}
void condition(){
if (distance_percent>65 && moist percent<85){
LCD_3();
digitalWrite(tank_pump,LOW);
digitalWrite(Watering_pump,HIGH);
sms1();
sms2();
delay(1000);}
else if(distance_percent<65 && moist_percent>85){
LCD_2();
digitalWrite(Tank_pump,HIGH);
digitalWrite(Watering_pump,LOW);
sms3();
sms();
delay(1000);}
else if(distance_percent>65 && moist_percent>85){
LCD_4();
digital_Write(Tank_pump,LOW);
digital_Write(Watering_pump,LOW);
sms1();
sms2();
delay(1000);}
else if(distance_percent<65 && moist_percent<85){
LCD_1();
digitalWrite(Tank_pump,HIGH);
digitalWrite(Watering_pump,HIGH);
void sms3();
void sms2();
delay(1000);}}
void LCD_1()
{
lcd.clear();
lcd.setCursor(0,0);
lcd.print("Tank level is");
lcd.print(distnace_percent);
lcd.print("%");
lcd.setCursor(0,1);
lcd.print("MOIST CONTENT=");
lcd.print(moist_percent);
lcd.print("%");
lcd.setCursor(0,2);
lcd.print("W_PUMP STATUS");
lcd.print("ON");
lcd.setCursor(0,3);
lcd.print("T_PUMP STATUS");
lcd.print("ON");
}
void LCD_2()
{
lcd.clear();
lcd.setCursor(0,0);
lcd.print("Tank level is");
lcd.print(distance_percent);
lcd.print("%");
lcd.setCursor(0,1);
lcd.print("MOIST CONTENT=");
lcd.print(moist_percent);
lcd.print("%");
lcd.setCorsor(0,2);
lcd.print("W_PUMP STATUS");
lcd.print("OFF");
lcd.setCursor(0,3);
lcd.print("T_PUMP STATUS");
lcd.print("ON");
}
void LCD_3()
{
lcd.clear();
lcd.setCursor(0,0);
lcd.print("Tank level is");
lcd.print(distance_percent);
lcd.print("%");
lcd.setCursor(0,1);
lcd.print("MOIST CONTENT=");
lcd.print(moist_percent);
lcd.print("%");
lcd.setCursor(0,2);
lcd.print("W_PUMP STATUS");
lcd.print("ON");
lcd.setCursor(0,3);
lcd.print("T_PUMP STATUS");
lcd.print("OFF");
}
void LCD_4()
{
lcd.clear();
lcd.setCursor(0,0);
lcd.print("Tank level is");
lcd.print(distance_percent);
lcd.print("%");
lcd.setCursor(0,1);
lcd.print("MOIST CONTENT=");
lcd.print(moist_percent);
lcd.print("%");
lcd.setCursor(0,2);
lcd.print("W_PUMP STATUS");
lcd.print("OFF");
lcd.print("T_PUMP STATUS");
lcd.print("OFF");}
