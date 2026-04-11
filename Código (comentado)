#include <LiquidCrystal.h> 

LiquidCrystal lcd(12, 11, 10, 5, 4, 3, 2);

// LEDs 
const int ledVerde    = 9;
const int ledAmarelo  = 8;
const int ledVermelho = 7;

const int buzzer = 6;

const int ldrPin = A0;

// CALIBRAÇÃO DO LDR
const int LDR_MIN  = 313;
const int LDR_MEIO = 850;
const int LDR_MAX  = 1013;

// LOSANGO CHEIO
byte losangoCheio[8] = {
  B00100,
  B01110,
  B11111,
  B11111,
  B11111,
  B01110,
  B00100,
  B00000
};

// LOSANGO VAZADO
byte losangoVazio[8] = {
  B00100,
  B01010,
  B10001,
  B10001,
  B10001,
  B01010,
  B00100,
  B00000
};

void setup() {
  pinMode(ledVerde, OUTPUT);
  pinMode(ledAmarelo, OUTPUT);
  pinMode(ledVermelho, OUTPUT);
  pinMode(buzzer, OUTPUT);

  lcd.begin(16, 2);

  lcd.createChar(0, losangoCheio);
  lcd.createChar(1, losangoVazio);

  lcd.clear();

// Boas-Vindas
  lcd.setCursor(0, 0);
  lcd.write(byte(0));

  String nome = " PRISMA ";
  for (int i = 0; i < nome.length(); i++) {
    lcd.print(nome[i]);
    delay(100);
  }

  lcd.write(byte(0));

  lcd.setCursor(0, 1);
  String msg = "Seja bem-vindo!";
  for (int i = 0; i < msg.length(); i++) {
    lcd.print(msg[i]);
    delay(80);
  }

 // ANIMAÇÃO DOS LOSANGOS (cheio ↔ vazio)
  for (int i = 0; i < 7; i++) {

    // LOSANGO CHEIO 
    lcd.setCursor(0, 0);
    lcd.write(byte(0));

    lcd.setCursor(9, 0);
    lcd.write(byte(0));

    delay(330);

    // LOSANGO VAZIO 
    lcd.setCursor(0, 0);
    lcd.write(byte(1));

    lcd.setCursor(9, 0);
    lcd.write(byte(1));

    delay(220); 
}
  lcd.clear();
}

void loop() {

  int leitura = analogRead(ldrPin);
  int luminosidade;

// MAPEAMENTO 
  if (leitura <= LDR_MEIO) {
    luminosidade = map(leitura, LDR_MIN, LDR_MEIO, 0, 50);

  } else {
    luminosidade = map(leitura, LDR_MEIO, LDR_MAX, 50, 100);
  }

luminosidade = constrain(luminosidade, 0, 100);

// MOSTRAR LUZ
  lcd.setCursor(0, 0);
  lcd.print("Luz: ");
  lcd.print(luminosidade);
  lcd.print("%   ");

// STATUS COM 3 NÍVEIS
  if (luminosidade >= 40 && luminosidade <= 60) {
	// OK
    digitalWrite(ledVerde, HIGH);
    digitalWrite(ledAmarelo, LOW);
    digitalWrite(ledVermelho, LOW);

    lcd.setCursor(0, 1);
    lcd.print("Status: OK       ");

    noTone(buzzer);
  } 
  	else if ((luminosidade >= 30 && luminosidade < 40) || 
             (luminosidade > 60 && luminosidade <= 70)) {
    // ALERTA
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledAmarelo, HIGH);
    digitalWrite(ledVermelho, LOW);
    tone(buzzer, 250);
    delay(250);
    digitalWrite(ledAmarelo, LOW);

    lcd.setCursor(0, 1);
    lcd.print("Status: Alerta         ");

    noTone(buzzer);
    delay(250);
  } 
  	else {
    // PROBLEMA
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledAmarelo, LOW);
    digitalWrite(ledVermelho, HIGH);

    lcd.setCursor(0, 1);
    lcd.print("Status: Critico      ");

    tone(buzzer, 500);
    delay(3000);
    noTone(buzzer);
    delay(1000);
  }

  delay(250);
}
