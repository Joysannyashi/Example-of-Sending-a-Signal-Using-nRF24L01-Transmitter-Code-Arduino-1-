//Example-of-Sending-a-Signal-Using-nRF24L01-Transmitter-Code-Arduino-1-
#include <SPI.h>
#include <nRF24L01.h>
#include <RF24.h>

RF24 radio(9, 10);  // CE pin 9, CSN pin 10
const byte address[6] = "00001";  // Address for communication

void setup() {
  radio.begin();
  radio.openWritingPipe(address);  // Set the address for the transmitter
  radio.setPALevel(RF24_PA_MIN);   // Set power level to low
}

void loop() {
  const char text[] = "Hello";
  radio.write(&text, sizeof(text));  // Send the message
  delay(1000);  // Send every second
}
