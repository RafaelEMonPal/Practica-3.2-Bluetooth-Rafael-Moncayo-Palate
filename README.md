# Practica-3.2-Bluetooth-Rafael-Moncayo-Palate

## Codi de la pràctica

```cpp

#include <Arduino.h>

#include "BluetoothSerial.h"
#if !defined(CONFIG_BT_ENABLED) || !defined(CONFIG_BLUEDROID_ENABLED)
#error Bluetooth is not enabled! Please run `make menuconfig` to and enable it
#endif
BluetoothSerial SerialBT;
void setup() {
Serial.begin(115200);
SerialBT.begin("1234"); //Bluetooth device name
Serial.println("The device started, now you can pair it with bluetooth!");
}
void loop() {
if (Serial.available()) {
SerialBT.write(Serial.read());
}
if (SerialBT.available()) {
Serial.write(SerialBT.read());
}
delay(20);
}

```

## Explicació del codi

Amb la llibreria "**BluetoothSerial**" creem un objecte bluetoothSerial que en sajudara a establir una conexió bluetooth amb cualsevol altre dispositiu capacitat per utilitzar bluetooth. El Setup com a tal és molt simple, iniciem la comunicació bluetooth i iniciem el serial amb la velocitat de monitor 115200. Seguidament en el Loop simplement utilitzem una comunicació Serial-SerialBluetooth per poder escriure en el dispositiu bluetooth i que aparegui per pantalla. 
La aplicació que utilitzarem per la comunicació entre el dispositiu i la ESP és la : "**Serial Bluetooth Terminal**" que la podrem trobar en la PlayStore.

