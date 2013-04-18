int lightPin = 0;  //define a pin for Photo resistor
int threshold = 1000; //threshold for photoresister 
int laser = 10; // laser connected to digital pin 10
int flash = 13; // flash connected to digital pin 13
int ready=1; //ready to flash
void setup(){
    Serial.begin(9600);  //Begin serial communcation
    pinMode(13, OUTPUT); // sets the digital pin 13 as output
    pinMode(10, OUTPUT);  // sets the digital pin 10 as output
    digitalWrite(laser, HIGH); //set laser on
}

void loop(){
  delay(1000); //delay of serial numbers 
    
    Serial.println(analogRead(lightPin)); //read photoresister
    if(analogRead(lightPin) > threshold && ready==1){  //if threshold is less than 1000  (when laser hits the photoresister) keep laser on
      digitalWrite(laser, LOW); //print low in serial
      . //if threshold is higher than 1000 (if laser does not hit photoresister)
       Serial.println("high"); //print high in serial
       delay(1000); //flash delay
      digitalWrite(flash, LOW); //turn flash off
      ready=0; //reset 
     }

    
}
