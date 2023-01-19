/*
Rajj YT 
Full vedio available on Youtube :-
https://youtu.be/CnH8NwcUiwM

link for Servo Library
https://github.com/arduino-libraries/Servo

link for Lcd library
https://github.com/arduino-libraries/LiquidCrystal

Circuit diagram :-
https://github.com/usmanrajj/LCD-Servo-with-Arduino
*/
#include <LiquidCrystal.h>      // Add this Library
#include <Servo.h>              // Add this Library

int rs = 11;  // connect RS pin to digital pin 11
int e = 12;   // connect  E pin to digital pin 12
int d4 = 4;   // connect d4 pin to digital pin 4
int d5 = 5;   // connect d5 pin to digital pin 5
int d6 = 6;   // connect d6 pin to digital pin 6
int d7 = 7;   // connect d7 pin to digital pin 7
int s1=9;     // Connect servo1 pin to digital pin 9
int s2=10;    // Connect servo2 pin to digital pin 10

Servo servo1;   // Create object named servo1
Servo servo2;   // Create object named servo2
LiquidCrystal lcd(rs, e, d4, d5, d6, d7);   // sequence must be same

int angle1=0;       // Variable to save Angle1 initially 0'
int angle2=180;     // Variable to save Angle2 initially 180'

void setup() {
  Serial.begin(9600);
  lcd.begin(16, 2);               // 16 colums & 2 rows
  lcd.print("Welcome, Rajj YT");  // show this line display on line
  lcd.setCursor(0, 1);            // move cursor to next line
  lcd.print("LCD +Servo Motor");  // show this line on display
  servo1.attach(s1);
  servo2.attach(s2);
  servo1.write(angle1);       // Set Servo1 Motor at an angle (angle1)
  servo2.write(angle2);       // Set Servo2 Motor at an angle (angle2)
  delay(2000);                // Wait for 2 Second to start this Program
}
void loop() {
  int i=0;

//  1st LOOP

  while(i<180){
  lcd.clear();                  // Clear All
  servo1.write(angle1);         // Rotate Servo1 at an angle ->(angl1)
  servo2.write(angle2);         // Rotate Servo2 at an angle ->(angl2)
  
  // Show on LCD 16x2 Screen

  lcd.print("Servo1 Angle ");         // Show this line on LCD Module
  lcd.print(angle1);                  // Show angle2 value on LCD Module
  lcd.setCursor(0, 1);                // Move cursor to next line
  lcd.print("Servo2 Angle ");         // Show this line on LCD Module
  lcd.print(angle2);                  // Show angle1 value on LCD Module
 
  // Show on Serial Monitor

Serial.print("Servo 1 Angle : ");     // Show this line on Computer Screen(Serial Monitor)
Serial.print(angle1);                 // Show angle1 value on Computer Screen(Serial Monitor)
Serial.print(" ,\tServo 2 Angle : "); // Show this line on Computer Screen(Serial Monitor)
Serial.println(angle2);               // Show angle2 value on Computer Screen(Serial Monitor)
  
  i++;                                // i=i+1
  angle1++;                           // angle1=angle1+1
  angle2--;                           // angle1=angle1-1
  delay(10);                         // Wait for 10 milisecond to start again this Loop
 }

//  2nd LOOP

  while(i>=0){
  lcd.clear();                  // Clear All
  servo1.write(angle1);         // Rotate Servo1 at an angle ->(angl1)
  servo2.write(angle2);         // Rotate Servo2 at an angle ->(angl2)

  // Show on LCD 16x2 Screen
  
  lcd.print("Servo1 Angle ");         // Show this line on LCD Module
  lcd.print(angle1);                  // Show angle2 value on LCD Module
  lcd.setCursor(0, 1);                // Move cursor to next line
  lcd.print("Servo2 Angle ");         // Show this line on LCD Module
  lcd.print(angle2);                  // Show angle1 value on LCD Module
 
  // Show on Serial Monitor

Serial.print("Servo 1 Angle : ");     // Show this line on Computer Screen(Serial Monitor)
Serial.print(angle1);                 // Show angle1 value on Computer Screen(Serial Monitor)
Serial.print(" ,\tServo 2 Angle : "); // Show this line on Computer Screen(Serial Monitor)
Serial.println(angle2);               // Show angle2 value on Computer Screen(Serial Monitor)

  i--;                                // i=i-1
  angle1--;                           // angle1=angle1-1
  angle2++;                           // angle2=angle2+1
  delay(10);
  }
}