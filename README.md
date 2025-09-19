# Auto Cut-off Charger By Time
###### Designed and simulated an Auto Cut-off Charger using Proteus, where the charging process is automatically stopped after a predefined time, ensuring battery protection and efficient energy usage.
---
## Here is the references...

Circuit Connections in Proteus :-

<img src=https://github.com/lingeshkumarkamaraj/Auto-Cut-off-Charger-By-Time/blob/main/1.png> 
<img src=https://github.com/lingeshkumarkamaraj/Auto-Cut-off-Charger-By-Time/blob/main/2.png> 
<img src=https://github.com/lingeshkumarkamaraj/Auto-Cut-off-Charger-By-Time/blob/main/3.png> 
<img src=https://github.com/lingeshkumarkamaraj/Auto-Cut-off-Charger-By-Time/blob/main/4.png>
<img src=https://github.com/lingeshkumarkamaraj/Auto-Cut-off-Charger-By-Time/blob/main/5.png> 

Working :- 

[<img width="300" height="300" src="https://img.icons8.com/color/96/start.png" alt="video"/>](https://youtu.be/7X1-UiQyeZ4)


---
Code :-
```

#include<LiquidCrystal.h>
LiquidCrystal lcd(13, 12, 11, 10, 9, 8);
int h = 0, m = 0, s = 0, st = 0;

void setup() {
  lcd.begin(16,2);
  pinMode(5,OUTPUT);
  pinMode(0,INPUT);
  pinMode(1,INPUT);
  pinMode(2,INPUT);
  pinMode(3,INPUT);
}

void loop() {
  int a, b, c;
  a = digitalRead(0);
  b = digitalRead(1);
  c = digitalRead(2);
  st = digitalRead(3);
  if(a == 1)
  {
    h++;
    delay(1000);
  }
  else if(b == 1)
  {
    m++;
    delay(1000);
    if(m == 60)
    {
      m=0;
      h++;
      delay(1000);
    }
  }
  else if(c == 1)
  {
    s++;
    delay(1000);
    if(s == 60)
    {
      s=0;
      m++;
      delay(1000);
    }
  }
  
  else if(st == 1)
  {
    if(s!=0)
    {
      digitalWrite(5,HIGH);
      s--;
      delay(1000);
    }
    else if(s==0 && m!=0)
      {
        m--;
        s=59;
      }
    else if(m==0 && h!=0)
    {
      h--;
      m=59;
    }
    else if(h == 0 && m == 0 && s == 0)
    {
      digitalWrite(5, LOW);
    }

    lcd.setCursor(0,0);
    lcd.print(" ");
    lcd.print("h:");
    lcd.print(h);
    lcd.print("m:");
    lcd.print(m);
    lcd.print("s:");
    lcd.print(s);
    lcd.print(" ");
  }

  lcd.setCursor(0,0);
    lcd.print(" ");
    lcd.print("h:");
    lcd.print(h);
    lcd.print("m:");
    lcd.print(m);
    lcd.print("s:");
    lcd.print(s);
    lcd.print(" ");
}


```
---
[PROTEUS FILE](https://github.com/lingeshkumarkamaraj/Auto-Cut-off-Charger-By-Time/blob/main/Charge%2026.pdsprj)
---
