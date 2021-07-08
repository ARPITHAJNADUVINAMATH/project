#project
#include<LiquidCrystal.h>
LiquidCrystal lcd(13,12,11,10,9,8);

#define in 3
#define out 4
#define relaymotor1 2
#define relaybulb1 5
#define relaymotor2 6
#define relaybulb2 7
#define relaymotor3 A0
#define relaybulb3 A1
#define relaymotor4 A2
#define relaybulb4 A3
int count=0;

void IN()
{
    count++;
    lcd.clear();
    lcd.print("Person In Room:");
    lcd.setCursor(0,1);
    lcd.print(count);
    delay(1000);
}

void OUT()
{
  if(count>0){
  count--;
  }
    lcd.clear();
    lcd.print("Person In Room:");
    lcd.setCursor(0,1);
    lcd.print(count);
    delay(1000);
}

void setup()
{
 Serial.begin(9600);
  lcd.begin(16,2);
  lcd.print("Visitor Counter");
  delay(2000);
  pinMode(in, INPUT);
  pinMode(out, INPUT);
  pinMode(relaymotor1, OUTPUT);
  pinMode(relaybulb1, OUTPUT);
  pinMode(relaymotor2, OUTPUT);
  pinMode(relaybulb2, OUTPUT);
  pinMode(relaymotor3, OUTPUT);
  pinMode(relaybulb3, OUTPUT);
  pinMode(relaymotor4, OUTPUT);
  pinMode(relaybulb4, OUTPUT);
  lcd.clear();
  lcd.print("Person In Room:");
  lcd.setCursor(0,1);
  lcd.print(count);
}

void loop()
{  
    Serial.println("no");

  Serial.println(digitalRead(in));
  //delay(10000);
  if(digitalRead(in)==0)
  IN();
  if(digitalRead(out)==0)
  OUT();
  
  if(count<=0)
  {
    lcd.clear();
    digitalWrite(relaymotor1,LOW);
    digitalWrite(relaybulb1, LOW);
    digitalWrite(relaymotor2, LOW);
    digitalWrite(relaybulb2, LOW);
    digitalWrite(relaymotor3, LOW);
    digitalWrite(relaybulb3, LOW);
    digitalWrite(relaymotor4, LOW);
    digitalWrite(relaybulb4, LOW);
    lcd.clear();
    lcd.print("Nobody In Room");
    lcd.setCursor(0,1);
    lcd.print("Light Is Off");
    delay(200);
  }
  
  else
  {
    if(count==1){
      digitalWrite(relaymotor1, HIGH);
    digitalWrite(relaybulb1, HIGH);
    digitalWrite(relaymotor2, LOW);
    digitalWrite(relaybulb2, LOW);
    digitalWrite(relaymotor3, LOW);
    digitalWrite(relaybulb3, LOW);
    digitalWrite(relaymotor4, LOW);
    digitalWrite(relaybulb4, LOW); 
    }
    if(count==2){
       digitalWrite(relaymotor1, HIGH);
    digitalWrite(relaybulb1, HIGH);
    digitalWrite(relaymotor2, HIGH);
    digitalWrite(relaybulb2, HIGH);
    digitalWrite(relaymotor3, LOW);
    digitalWrite(relaybulb3, LOW);
    digitalWrite(relaymotor4, LOW);
    digitalWrite(relaybulb4, LOW); 
    }
    if(count==3){
      digitalWrite(relaymotor1, HIGH);
    digitalWrite(relaybulb1, HIGH);
    digitalWrite(relaymotor2, HIGH);
    digitalWrite(relaybulb2, HIGH);
    digitalWrite(relaymotor3, HIGH);
    digitalWrite(relaybulb3, HIGH);
    digitalWrite(relaymotor4, LOW);
    digitalWrite(relaybulb4, LOW); 
           }
   
  

  if(count>3)
  {
    digitalWrite(relaymotor1, HIGH);
    digitalWrite(relaybulb1, HIGH);
    digitalWrite(relaymotor2, HIGH);
    digitalWrite(relaybulb2, HIGH);
    digitalWrite(relaymotor3, HIGH);
    digitalWrite(relaybulb3, HIGH);
    digitalWrite(relaymotor4, HIGH);
    digitalWrite(relaybulb4, HIGH); 
  }
   
}
}
LiquidCrystal lcd(13,12,11,10,9,8);

#define in 3
#define out 4
#define relaymotor1 2
#define relaybulb1 5
#define relaymotor2 6
#define relaybulb2 7
#define relaymotor3 A0
#define relaybulb3 A1
#define relaymotor4 A2
#define relaybulb4 A3
