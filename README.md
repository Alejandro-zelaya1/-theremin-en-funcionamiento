# -theremin-en-funcionamiento
tarea de robotica de edgardo alejandro

El theremin normalmente usa sensores de capacitancia o distancia (ultrasónicos, infrarrojos, etc.) para detectar el movimiento de la mano. Aquí hay algunas opciones que podrías considerar:

Sensor ultrasónico (HC-SR04): Usa ondas de sonido para medir la distancia. Funciona bien para detectar la posición de la mano.

Sensor infrarrojo (GP2Y0A21YK0F): Mide la distancia usando luz infrarroja. Puede ser más preciso que el ultrasónico.

Sensor de proximidad capacitivo (TTP223): Detecta la presencia de la mano sin necesidad de contacto, similar al theremin original.

LIDAR (VL53L0X): Usa láser para medir la distancia con alta precisión.

Acelerómetro (MPU6050): Puede medir el movimiento y la inclinación de la mano en lugar de la distancia.




acontinuacion el codigo que use para su funciona miento 

#define TRIG_PIN 9
#define ECHO_PIN 10
#define BUZZER_PIN 3

void setup() {
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(BUZZER_PIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // Enviar pulso al sensor ultrasónico
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  // Recibir eco y calcular distancia
  long duration = pulseIn(ECHO_PIN, HIGH, 30000);
  int distance = duration * 0.034 / 2; // Convertir a cm

  Serial.print("Distancia: ");
  Serial.println(distance);

  // Aumentamos el rango de detección hasta 50 cm
  if (distance > 2 && distance < 100) { 
    digitalWrite(BUZZER_PIN, HIGH); // ENCENDER buzzer
  } else {
    digitalWrite(BUZZER_PIN, LOW); // APAGAR buzzer
  }

  delay(100);
}
