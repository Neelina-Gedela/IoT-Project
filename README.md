# IoT-Project
int inputPin = 2; // choose the input pin (for PIR sensor)
int pirState = LOW; // we start, assuming no motion detected
int val = 0; // variable for reading the pin status
const int Input1=8;
int State1=0;

void setup() {
 pinMode(inputPin, INPUT); // declare sensor as input0
 Serial.begin(9600);
}
void loop(){
 val = digitalRead(inputPin); // read input value
 if (val == HIGH) { // check if the input is HIGH
 if (pirState == LOW) {
 // we have just turned on
 Serial.println("Motion detected!");
 // We only want to print on the output change, not state
 pirState = HIGH;
 {
 Serial.println("AT\r");
  delay(1000);
  Serial.println("AT+CMGF=1\r");
  delay(1000);
  Serial.println("AT+CMGS=\"+917330879987\"\r");
  delay(1000);
  Serial.println("THEFT ALERT IN HOME");
  delay(1000);
  Serial.println((char)26);
  delay(100);
}
 }
 } else {
  if (pirState == HIGH){
 // we have just turned of
 Serial.println("Motion ended!");
 // We only want to print on the output change, not state
 pirState = LOW;
 }
 }
}
  
