// Define pin numbers for the HC-SR04 and Relay
const int trigPin = 9;  // Trigger pin for the HC-SR04
const int echoPin = 10; // Echo pin for the HC-SR04
const int relayPin = 8; // Pin connected to relay

void setup() {
  // Setup sensor pins and relay pin
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(relayPin, OUTPUT);
  
  // Initialize the relay as off
  digitalWrite(relayPin, LOW);

  // Initialize Serial communication (for debugging)
  Serial.begin(9600);
}

void loop() {
  // Sends a 10 micro sec pulse to the trigger pin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Read the pulse duration on the echo pin
  long duration = pulseIn(echoPin, HIGH);

  // dist calculation in cm
  long distance = (duration * 0.034) / 2;

  // Print the distance to the Serial Monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  // within 10 cm light turns on
  if (distance >= 10) {
    digitalWrite(relayPin, HIGH);  // relay on, Bulb on
    Serial.println("Object detected within 2 cm - Relay ON");
  } else {
    digitalWrite(relayPin, LOW);   // relay off, Bulb off
    Serial.println("No object within 2 cm - Relay OFF");
  }

  // to avoid excessive readings
  delay(500);
}
