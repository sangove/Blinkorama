# Blinkorama
Blinkorama Project Code

/* GDES3015 Wearable Computing
   1 button used to control 1 LED
*/

//switch pin
int switchPin = 12;
//switch value
int switchValue;

int oldSwitchValue;
//green led
int green = 13;
//yellow 1
int yellowOne = 5;
//yellow 2
int yellowTwo = 11;
//yellow 3
int yellowThree = 10;
//red
int red = 9;
//brightness
int brightness = 0;
int fadeAmount = 5;

void setup() {
  // put your setup code here, to run once:
  pinMode(switchPin, INPUT);
  pinMode(green, OUTPUT);
  pinMode(yellowOne, OUTPUT);
  pinMode(yellowTwo, OUTPUT);
  pinMode(yellowThree, OUTPUT);
  pinMode(red, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
  switchValue = digitalRead(switchPin);
  Serial.println(switchPin);
  if (switchValue != oldSwitchValue && switchValue == 0) {
    digitalWrite(green, LOW);
    lockedKnees();
  } else if (switchValue == 1){
    digitalWrite(green, HIGH);
    digitalWrite(yellowOne, LOW);
    digitalWrite(yellowTwo, LOW);
    digitalWrite(yellowThree, LOW);
    digitalWrite(red, LOW);
  }
  oldSwitchValue = switchValue;

}
void lockedKnees() {
  //sequence that happens when knee is stright

  for (int fadeValue = 0 ; fadeValue <= 255; fadeValue += 5) {
    // sets the value (range from 0 to 255):
    analogWrite(yellowOne, fadeValue);
    // wait for 30 milliseconds to see the dimming effect
    delay(10);
  }
  
  for (int fadeValue = 0 ; fadeValue <= 255; fadeValue += 5) {
    // sets the value (range from 0 to 255):
    analogWrite(yellowTwo, fadeValue);
    // wait for 30 milliseconds to see the dimming effect
    delay(10);
  }
  
  for (int fadeValue = 0 ; fadeValue <= 255; fadeValue += 5) {
    // sets the value (range from 0 to 255):
    analogWrite(yellowThree, fadeValue);
    // wait for 30 milliseconds to see the dimming effect
    delay(10);
  }
 {
  digitalWrite(yellowOne, LOW);
  digitalWrite(yellowTwo, LOW);
  digitalWrite(yellowThree, LOW);
 }
  //delay(500);
{
  digitalWrite(red, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(150);                       // wait for a second
  digitalWrite(red, LOW);    // turn the LED off by making the voltage LOW
  delay(150);                       // wait for a second
digitalWrite(red, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(150);                       // wait for a second
  digitalWrite(red, LOW);    // turn the LED off by making the voltage LOW
  delay(150);                       // wait for a second
  digitalWrite(red, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(150);                       // wait for a second
  digitalWrite(red, LOW);    // turn the LED off by making the voltage LOW
  delay(150);                       // wait for a second
  digitalWrite(red, HIGH);
}
}

