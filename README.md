const int potPin = A0;      // Pino analógico onde o potenciômetro está conectado
const int ledCount = 9;    // Número de LEDs
const int ledPins[ledCount] = {2, 3, 4, 5, 6, 7, 8, 9, 10}; // Pinos digitais conectados aos LEDs

void setup() {
  // Inicializa os pinos dos LEDs como saída
  for (int i = 0; i < ledCount; i++) {
    pinMode(ledPins[i], OUTPUT);
  }
}

void loop() {
  int potValue = analogRead(potPin);    // Lê o valor do potenciômetro (0 a 1023)
  int ledIndex = map(potValue, 0, 1023, 0, ledCount - 1); // Mapeia o valor do potenciômetro para o número de LEDs

  // Aciona os LEDs com base no valor do potenciômetro
  for (int i = 0; i < ledCount; i++) {
    if (i <= ledIndex) {
      digitalWrite(ledPins[i], HIGH);  // Acende o LED
    } else {
      digitalWrite(ledPins[i], LOW);   // Apaga o LED
    }
  }

  delay(10); // Pequeno atraso para evitar leituras rápidas demais
}
