#include <LiquidCrystal.h>

// Initialize the LCD with the appropriate pin numbers
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

int sensorPin = A0; // Sensor connected to A0
int potValue = 0;   // Variable to store the analog reading
int buzzer = 13;    // Buzzer connected to D13

// Minimum gas concentration value to detect gas
const int gasThreshold = 500;

void setup() {
    // Initialize the LCD
    lcd.begin(16, 2); // lcd rows and columns

    // Set the buzzer pin as output
    pinMode(buzzer, OUTPUT);
}

void loop() {
    // Read the value from the sensor
    potValue = analogRead(sensorPin);

    // Check if the gas concentration exceeds the threshold
    if (potValue > gasThreshold) {
        // Center and display "Warning!!! RUN" on the first row
        lcd.setCursor(0, 0);
        lcd.print("                "); // Clear the line
        lcd.setCursor(1, 0);
        lcd.print("WARNING !!! RUN");

        // Display "Gas is Detected" on the second row
        lcd.setCursor(0, 1);
        lcd.print("GAS IS DETECTED");

        // Sound the buzzer high 5 times within 2 seconds
        for (int i = 0; i < 5; i++) {
            digitalWrite(buzzer, HIGH); // Turn the buzzer on
            delay(500);                 // Wait for 200 milliseconds
            digitalWrite(buzzer, LOW);  // Turn the buzzer off
            delay(200);                 // Wait for 200 milliseconds
        }
    } else {
        // Center and display "No Gas Detected" on the first row
        lcd.setCursor(0, 0);
        lcd.print("                "); // Clear the line
        lcd.setCursor(1, 0);
        lcd.print("NO GAS DETECTED");

        // Display "We are Safe" on the second row
        lcd.setCursor(0, 1);
        lcd.print("  We are Safe  ");
        
        // Turn the buzzer off
        digitalWrite(buzzer, LOW);
    }

    // Wait for 1 second before the next reading
    delay(1000);
}
