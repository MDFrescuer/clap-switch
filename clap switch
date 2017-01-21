// The date of beging: 17-1-2017 22:31.
// The creator: MDF RESCUER YouTube.
// Conditions: This is an Open Source Project. Feel free to use this project for your fun and benefits, but
// I have only one condition, always let people know from where this project originates.
// Anyway, subscribe to my MDF RESCUR YouTube channel!

// SETUP IN THE ARDUINO IDE:
// Do this: https://create.arduino.cc/projecthub/arjun/programming-attiny85-with-arduino-uno-afb829
// My changes needed to be setup in the IDE:
// Clock: "Internal 1 MHz"
// No need to burn the bootloader and probably it will save some power.

// pin2 is analog input 3
// 1, measuring of how long is there log 1 on the an.pin3

// INSTALLING AND SETTING THE VARIABLES:
int b = 0; // value stors a variable of some time while a sound was present = we had log 1 on an. pin3
boolean latch1 = false; // first condition accomplished is true:
boolean latch2 = false; // second condition accomplished is true:
boolean latch3 = false; // third condition accomplished is true:
boolean svitch = false; //stores the value if the light is on has value of true...
int treshold = 1000; // here we define the treshold value, basicaly we set from what level of sound we consider it as log1 or log0

void setup() { 
pinMode(4, OUTPUT); // initialize pin 4 as dig output for controlling the relay.
pinMode(A3, INPUT); // initialize pin 3 as the analog input for sensing the DC sound peeks from the microphone
} // INSTALLING AND SETTING THE VARIABLES ENDS



void loop() {
b++; // basicaly this caunting we will use for measurng the time betwen the claps.

  if (analogRead(3) <= treshold) { // minimum time measuring the clap period  { // whatever clap is detected the prohram will get here
  //PROTECTION AGAINST UNWANTED SOUNDS:
  delay(1); if (analogRead(3) > treshold) {latch1 = false; latch2 = false; latch3 = false;} // here we detect too short flash of sound and we immediately latch everithing.
  delay(120); //  so we detedted a flash of sound, now we wait some time because if it is a clap, it must be gone in this period of time we wait. if there will be sound again detected after this delay it will not open our latches because the time period betwen the peeaks is too short and thus we detected unwanted sound.
  if (analogRead(3) <= treshold-100) {latch1 = false; latch2 = false; latch3 = false;} delay(1); // this protection detects longer peaks of sound (which obviosly doesn't belong to a clap) and latches everithing
  if (analogRead(3) <= treshold-100) {latch1 = false; latch2 = false; latch3 = false;} delay(1); // this protection detects longer peaks of sound (which obviosly doesn't belong to a clap) and latches everithing
  if (analogRead(3) <= treshold-100) {latch1 = false; latch2 = false; latch3 = false;} delay(1); // this protection detects longer peaks of sound (which obviosly doesn't belong to a clap) and latches everithing
  if (analogRead(3) <= treshold-100) {latch1 = false; latch2 = false; latch3 = false;} delay(1); // this protection detects longer peaks of sound (which obviosly doesn't belong to a clap) and latches everithing
  if (analogRead(3) <= treshold-100) {latch1 = false; latch2 = false; latch3 = false;} delay(1); // this protection detects longer peaks of sound (which obviosly doesn't belong to a clap) and latches everithing
  //PROTECTION AGAINST UNWANTED SOUNDS ENDS.

  // LATCH SYSTEM - BESICALY DETECTING THE RIGHT PERIODS OF TIME BETWEN THE SOUND PEEKS:
  if (b <= 900 || b >= 2500 && latch1 == true) { latch1 = false; latch2 = false; latch3 = false; b = 0;}// protection against detected false sound periods of time. if is detected we latch all latches
  if (latch1 == true && latch2 == true && latch3 == false && b >900 && b < 2500) {
  latch1 = false; latch2 = false; latch3 = false; // after unlatching we again latch because we want to restart the process of unlatching 
  if (svitch == false) svitch = true; else {svitch = false;}  b = 0;}  // detected 3 claps // we change the state of the value svitch
  if (latch1 == true && latch2 == false && latch3 == false && b >900 && b < 2500) {latch2 = true; b = 0;}  // detected 2 claps
  if (latch1 == false && latch2 == false && latch3 == false) { latch1 = true; b = 0;} // detected 1 clap and reseting the value b to start count out of the time betwen the claps
  if (latch3 == true) {latch1 = false; latch2 = false; latch3 = false;} //taking acttion when everithing is unlatched
  if (svitch == true) digitalWrite(4, HIGH); // dig pin 4 wchich is pin 3 on the chip changes it state to log 1 to turn on the relay and the light
  if (svitch == false) digitalWrite(4, LOW);  // dig pin 4 wchich is pin 3 on the chip changes it state to log 0 to turn off the relay and the light
  } // when we have measured the right periof of time of log 1 then program does this.
  // LATCH SYSTEM ENDS

if (b >= 5100) {latch1 = false; latch2 = false; latch3 = false; b = 0; }// reseting this value due to it's fyzical limitation and basicaly too much time betwen the claps detected so we latch all latches
} // main look ends.


































// TROUBLESHOTING TOOLS:
// Put it into main loop. on pin 3 you will get digitalized value from pin 2 (an input):
// if  (analogRead(A3) <= 1010) digitalWrite(4, HIGH);
// if  (analogRead(A3) > 1010) digitalWrite(4, LOW)


// Put LED through a resiostor on pin 3 and this will turn on and off the output:
// digitalWrite(3, HIGH);   // turns the relay on
// delay(500);             // waits
// digitalWrite(3, LOW);   // turns the relay on
// delay(500);             // waits
