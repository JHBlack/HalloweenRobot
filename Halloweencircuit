#include <Servo.h>

// Define pin numbers
const int trigPin = 7;
const int echoPin = 6;
const int pirPin = 12;
const int servoPin1 = 5;
const int servoPin2 = 3;

// Create servo objects
Servo servo1;
Servo servo2;

void setup() {
  // Initialize serial communication
  Serial.begin(9600);

  // Initialize ultrasonic sensor pins
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  // Initialize PIR sensor pin
  pinMode(pirPin, INPUT);

  // Attach servo motors to their respective pins
  servo1.attach(servoPin1);
  servo2.attach(servoPin2);

  // Set initial position of servo motors
  servo1.write(0);
  servo2.write(0);
}

void loop() {
  // Check if motion is detected by the PIR sensor
  if (digitalRead(pirPin) == HIGH) {
    // Measure distance from the ultrasonic sensor
    long duration, distance;
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);
    duration = pulseIn(echoPin, HIGH);
    distance = (duration / 2) / 29.1;

    // Check if the target is within 60 inches (152.4 cm)
    if (distance >= 152.4) {
      Serial.print("Target detected at ");
      Serial.print(distance);
      Serial.println(" cm");

      // Rotate servo motors by 90 degrees
      servo1.write(90);
      servo2.write(90);
      delay(1000); // Wait for 1 second

      // Reset servo motors to initial position
      servo1.write(0);
      servo2.write(0);
    }
  }
}
