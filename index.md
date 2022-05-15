# Basic of Arduino IDE

<br>

## Functions at startup

### a)  setup()
    
   - This function is called at the beginning of the sketch.
   - It is used for initializing variables, pin modes etc.
   - It runs only once after each power up, or when the Arduino board resets.

### b)  loop()
    
   - Once the setup function is completed, the loop function is executed over and over continuously. 

<br>

## Functions for using GPIO

### a)  `pinMode(pin, mode)`

   - `pin` : The pin for which a specific mode is selected.
   - `mode` : The mode for the pin specified in the function. It can be INPUT, INPUT PULLUP or OUTPUT.
   - This function is used to configure the pin specified to behave as Input (INPUT), Input with pull up resistor (INPUT_PULLUP), or Output (OUTPUT).
   - Example pinMode(3,INPUT) configures digital pin 3 as an input pin.

### b)  `digitalRead(digital_pin)`

   - `digital_pin` : The digital pin which is to be read.
   - This function is used to read the digital signal from the specified digital pin (digital_pin).
   - Arduino UNO board has 14 digital pins 0 to 13.
   - The function returns either HIGH or LOW.
   - Example `digitalRead(5)` reads value on pin 5.

 

### c)  `digitalWrite(pin, value)`

   - `pin` : The digital pin to which value is to be written.
   - `value` : Can be HIGH or LOW.
   - This function is used to write a HIGH or a LOW value to a digital pin.
   - Example digitalWrite(4, HIGH) makes the pin 4 HIGH.


#### Blinking on-board LED connected to pin 13 of Arduino UNO

```cpp
//Setup is run once at the start (Power-On or Reset) of sketch 

void setup()
{
    pinMode(13, OUTPUT); // Pin 13 is defined as Output 
}

// Loop runs over and over after the startup function 

void loop()
{
    digitalWrite(13, HIGH); // Make pin 13 High, LED ON 
    delay(1000); // Wait for 1 second 
    digitalWrite(13, LOW); // Make pin 13 Low, LED OFF
    delay(1000); // Wait for 1 second 
}

```

### d)  analogRead(analog_pin)

   - `analog_pin` : The analog pin whose value is to be read.
   - This function is used to read the analog signal from the specified analog pin (analog_pin).
   - UNO board has 6 ADC channels A0 to A5.
   - The function returns an integer value in the range of 0 to 1023.
   - Example analogRead(A3) reads the value on analog pin A3.

#### Reading analog value from an analog sensor connected to pin A1 of Arduino and displaying the ADC value on serial monitor of Arduino
```cpp
/* Setup is run once at the start (Power-On or Reset) of sketch */
void setup()
{
    Serial.begin(9600); // opens serial port, sets data rate to 9600 bps 
}

/* Loop runs over and over after the startup function */

void loop()
{
    int adc_val;
    adc_val = analogRead(A1); // Read analog signal present on pin A1 
    Serial.print("ADC value is : "); // Print 
    Serial.println(adc_val); // Print with \r\n 
    delay(5000); // Wait for 5 seconds 
}
```

### e)  analogWrite(pin,value)

   - `pin` : The analog pin to which value is to be written.
   - `value` : Can be any number between 0 to 255. 0 being 0% duty cycle and 255 being 100% duty cycle.
   - This function is used for generating PWM on PWM digital pins(pins 3,5,6,9,10,11 for Arduino UNO.
   - value can be any number between 0 to 255. 0 being 0% duty cycle and 255 being 100% duty cycle.
   - Example analogWrite(3, 128) generates a PWM wave of 50% duty cycle on pin 3.

#### Vary intensity of LED connected to pin 5 of Arduino by generating PWM wave of varying duty cycle

```cpp
/* Setup is run once at the start (Power-On or Reset) of sketch */
void setup()
{
    pinMode(5, OUTPUT);  /* Pin 5 is defined as Output */
}

/* Loop runs over and over after the startup function */
void loop()
{
    for(int i =0; i<256; i++)
     {
        analogWrite(5, i); /* Vary intensity of LED connected externally to pin 5 of Arduino */
        /* Vary the intensity by applying PWM of duty cycle varying from 0 to 100% (writing value 0 to 255) */
        delay(300); /* Wait for 300 milliseconds */
     }
}
```
