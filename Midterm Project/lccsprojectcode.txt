#include <LiquidCrystal.h>

// initialising lcd screen
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

//setting pins
int sensorPin = A0;    // select the input pin for the moisture Sensor
int tempPin = A1;

//initialisiing variables
int sensorValue = 0;  // variable to store the value coming from the sensor
int tempValue = 0;

/
void setup() {
  Serial.begin(9600); 
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);

  
}
//temperature input conversion
float getVoltage(int pin){

return(analogRead(pin) * .004882814);
} 


void loop() {


   // read the values from the sensors:
 sensorValue = analogRead(sensorPin);
 float tempValue = getVoltage(tempPin);            
 float tempReading = (tempValue - .5) * 100;

    // wait a bit 
 delay(100);
 // clear the screen
 lcd.clear();
 //set cursor
 lcd.setCursor(1, 0);
 //print
 lcd.print("CS 2018");
 lcd.setCursor(0, 1);
 lcd.print("Plug-in Plant");
 
 delay(4000);

 //Print soil moisture
 lcd.clear(); 
 lcd.setCursor(1, 0);
 lcd.print("Plant Moisture: ");
 lcd.setCursor(0, 1);
 lcd.print(sensorValue);

 //Print temperature
 delay(4000);
 lcd.clear();
 lcd.setCursor(1, 0);
 //print temperature
 lcd.print("Temperature:");
 lcd.setCursor(0, 1);
 lcd.print(tempReading);

 delay(4000);
  
   }



