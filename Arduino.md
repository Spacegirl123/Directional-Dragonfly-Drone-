//Importing Libarys

#include <Wire.h>
#include <BH1750.h>


// defining veribles

BH1750 lightMeter;
const int trigPin = 10;
const int echoPin = 13;
// defines variables
long duration;
int distance;
int data;


//Pins for Drone Motors A B C D

int motorA1 = 7;
int motorA2 = 6;

int motorB1 = 2;
int motorB2 = 3;

int motorC1 = 12;
int motorC2 = 11;

int motorD1 = 9;
int motorD2 = 8;


void setup() 
{ 
  // defining lights that act like eyes
  
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  
  // Defining Motors

  pinMode(motorA1, OUTPUT);
  pinMode(motorA2, OUTPUT);
  
  pinMode(motorB1, OUTPUT);
  pinMode(motorB2, OUTPUT);
  
  pinMode(motorC1, OUTPUT);
  pinMode(motorC2, OUTPUT);
  
  pinMode(motorD1, OUTPUT);
  pinMode(motorD2, OUTPUT);

  //defining sensors

//pinMode(8, OUTPUT);
//pinMode(7, OUTPUT);
pinMode(trigPin, OUTPUT); 
pinMode(echoPin, INPUT); 
Wire.begin();
  
  //lightMeter.begin();


  Serial.begin(9600);
  
  while (! Serial);
  Serial.println("direction");
} 


void loop(){
  // Clears the trigPin
digitalWrite(trigPin, LOW);
delay(2);
digitalWrite(trigPin, HIGH);
delay(10);
digitalWrite(trigPin, LOW);

duration = pulseIn(echoPin, HIGH);

distance= duration*0.034/2;

if (distance > 30){
  distance = 0;
}
 else{
Serial.println(7);
 }
//Serial.println("Distance:");
//Serial.println(distance);
 
//float lux = lightMeter.readLightLevel();
  

 // if (lux>700){
   
  //  lux = 1;
   
  //}

 // else{
   
  //  lux = 1;   
   
//  }




  while (Serial.available()){
   int data = Serial.read();
 

  
    if (data=='0'){
// left
    int speed2 = 20;
    int speed = 20;
  
  digitalWrite(5, HIGH);
  delay(1000);
  digitalWrite(motorA2, LOW); // Motor A Clockwise
  digitalWrite(motorA1, speed);

  digitalWrite(motorB1,speed); // Motor B Anti-Clockwise
  digitalWrite(motorB2, LOW);

  digitalWrite(motorC1, speed); // Motor C Clockwise
  digitalWrite(motorC2, LOW);

  digitalWrite(motorD2, speed); // Motor D Anti-Clockwise
  digitalWrite(motorD1, LOW);
delay(5000);


  
  digitalWrite(5, LOW);

  
  
digitalWrite(motorA2, LOW); // Motor A Clockwise
  digitalWrite(motorA1, LOW);

  digitalWrite(motorB2,LOW); // Motor B Anti-Clockwise
  digitalWrite(motorB1, LOW);

  digitalWrite(motorC1, LOW); // Motor C Clockwise
  digitalWrite(motorC2, LOW);

  digitalWrite(motorD1, LOW); // Motor D Anti-Clockwise
  digitalWrite(motorD2, LOW);

    }

    if (data=='1'){
  // right
 
    int speed2 = 20;
    int speed = 20;
  digitalWrite(4, HIGH);
  delay(1000);
  digitalWrite(motorA1, LOW); // Motor A Clockwise
  digitalWrite(motorA2, speed);

  digitalWrite(motorB2,speed); // Motor B Anti-Clockwise
  digitalWrite(motorB1, LOW);

  digitalWrite(motorC1, LOW); // Motor C Clockwise
  digitalWrite(motorC2, speed);

  digitalWrite(motorD1, speed); // Motor D Anti-Clockwise
  digitalWrite(motorD2, LOW);
  delay(5000);


  digitalWrite(4, LOW);
  
  
  digitalWrite(motorA2, LOW); // Motor A Clockwise
  digitalWrite(motorA1, LOW);

  digitalWrite(motorB2,LOW); // Motor B Anti-Clockwise
  digitalWrite(motorB1, LOW);

  digitalWrite(motorC1, LOW); // Motor C Clockwise
  digitalWrite(motorC2, LOW);

  digitalWrite(motorD1, LOW); // Motor D Anti-Clockwise
  digitalWrite(motorD2, LOW);
}

  
}
}
