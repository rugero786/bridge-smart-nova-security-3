int redLED = 2;
int greenLED = 3;
int buzzer = 6;
int doorBtn = 7;
int resetBtn = 8;
int ldr = A0;

bool alarmActive = false;

void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(doorBtn, INPUT);
  pinMode(resetBtn, INPUT);
  Serial.begin(9600);
}

void loop() {
  int doorState = digitalRead(doorBtn);
  int resetState = digitalRead(resetBtn);
  int lightValue = analogRead(ldr);

  if (!alarmActive) {
    if (lightValue > 600) {
      Serial.println("NIGHT MODE ON");
      digitalWrite(greenLED, HIGH);
      delay(500);
      digitalWrite(greenLED, LOW);
      delay(500);
    } else {
      digitalWrite(greenLED, HIGH);
      Serial.println("MONITORING ACTIVE");
    }
  }

  if (doorState == HIGH && !alarmActive) {
    alarmActive = true;
    Serial.println("INTRUDER DETECTED");

    for (int i = 0; i < 10; i++) {
      digitalWrite(redLED, HIGH);
      digitalWrite(buzzer, HIGH);
      delay(200);
      digitalWrite(redLED, LOW);
      digitalWrite(buzzer, LOW);
      delay(200);
    }

    digitalWrite(redLED, HIGH);
    digitalWrite(buzzer, HIGH);
    digitalWrite(greenLED, LOW);
  }

  if (resetState == HIGH) {
    alarmActive = false;
    digitalWrite(redLED, LOW);
    digitalWrite(buzzer, LOW);
    Serial.println("SYSTEM RESET");
  }
}
