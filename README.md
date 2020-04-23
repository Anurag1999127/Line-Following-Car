# Line-Following-Car
Line Following Car using Arduino
#define LS 2      // left sensor
#define RS 3      // right sensor
int en=8;
#define LM1 4       // left motor
#define LM2 5       // left motor
#define RM1 6       // right motor
#define RM2 7       // right motor

void setup()
{ 
  pinMode(LS, INPUT);
  pinMode(RS, INPUT);
  pinMode(LM1, OUTPUT);
  pinMode(LM2, OUTPUT);
  pinMode(RM1, OUTPUT);
  pinMode(RM2, OUTPUT);
}

void loop()
{  analogWrite(en, 127);
  if(!digitalRead(LS) && !digitalRead(RS))     // Move Forward
  { 
    analogWrite(LM1, 0);
    analogWrite(LM2, 175);
    analogWrite(RM1, 0);
    analogWrite(RM2, 175);
  }
  
  if((digitalRead(LS)<=0) && (digitalRead(RS)>=1))     // Turn right
  {
    analogWrite(LM1, 0);
    analogWrite(LM2, 0);
    analogWrite(RM1, 0);
    analogWrite(RM2, 175);
  }
  
  if(digitalRead(LS) && !(digitalRead(RS)))     // turn left
  {
    analogWrite(LM1, 0);
    analogWrite(LM2, 175);
    analogWrite(RM1, 0);
    analogWrite(RM2, 0);
  }
  
  if(
    (digitalRead(LS)) && (digitalRead(RS)))     // stop
  {
    digitalWrite(LM1, 0);
    digitalWrite(LM2, 0);
    digitalWrite(RM1, 0);
    digitalWrite(RM2, 0);
  }
}
