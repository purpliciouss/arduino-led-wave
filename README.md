# Knight Rider LED Chase Effect

A classic beginner Arduino Uno project where LEDs light up in sequence, creating a back-and-forth "wave" effect — inspired by the scanning red light from Knight Rider.

## Components Needed

- 1x Arduino Uno
- 6x LED
- 5x 330 Ω resistors
- 1x 220 Ω resistor (i used instead of a 330 Ω cause i didn't have enough resistors, no effect on the circuit)
- Breadboard
- 13x Jumper wires

## Circuit Connections

| LED | Arduino Pin | Resistor |
|-----|-------------|----------|
| LED 1 | Pin 2 | 330 Ω |
| LED 2 | Pin 3 | 330 Ω |
| LED 3 | Pin 4 | 330 Ω |
| LED 4 | Pin 5 | 330 Ω |
| LED 5 | Pin 6 | 330 Ω |
| LED 6 | Pin 7 | 330 Ω / 220 Ω |

Each LED's cathode (short leg) connects to Arduino's **GND** pin through a resistor. The anode (long leg) connects to its corresponding digital pin.

## How It Works

Inside the `loop()` function, the code lights up the LEDs in sequence (2 → 3 → 4 → 5 → 6 → 7) creating a forward wave, then repeats it in reverse (7 → 6 → 5 → 4 → 3 → 2). Since this runs continuously inside `loop()`, the effect never stops.

## code
```
int ledler[] = {2, 3, 4, 5 ,6 ,7};

void setup() {
  for(int i= 0; i<6; i++){
    digitalWrite(ledler[i], HIGH);
    delay(80);
    digitalWrite(ledler[i], LOW);
  }
}

void loop() {
  for(int j= 5; j>-1; j--){
    digitalWrite(ledler[j], HIGH);
    delay(80);
    digitalWrite(ledler[j], LOW);
  }
}
 ```

## Circuit Setup
<img width="444" height="256" alt="Screenshot 2026-07-03 at 13 16 10" src="https://github.com/user-attachments/assets/41ec5328-a9bb-49aa-8cb1-1b280d5e930a" />


## Notes

- The LED using the 220 Ω resistor may appear slightly brighter than the others; it does not affect the circuit's operation.
- If you change the pin numbers or number of LEDs, make sure to update the pin array in the code accordingly.
