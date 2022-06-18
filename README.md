# Experiment--08-Design-and-control-of-Mobile-robot-motion-
 

## AIM: 
To Design a wheel base for mobile robot and control the motion using forward and reverse motion 
 
### COMPONENTS REQUIRED:
1.	 Patch cables 
2.	L293D motor shield 
3.	Arduino Uno 
4.	USB Interfacing cable 
5.	Connecting wires 
6.	Wheels
7.	DC motor 


### THEORY: 
We can control the speed of the DC motor by simply controlling the input voltage to the motor and the most common method of doing that is by using PWM signal.


DC Motor Speed Control Input Voltage
PWM DC Motor Control
PWM, or pulse width modulation is a technique which allows us to adjust the average value of the voltage that’s going to the electronic device by turning on and off the power at a fast rate. The average voltage depends on the duty cycle, or the amount of time the signal is ON versus the amount of time the signal is OFF in a single period of time.
 

PWM Working Principle - Pulse Width Modulation How It Works
 
 

![image](https://user-images.githubusercontent.com/36288975/174224618-c8d83fea-4456-4706-9974-c8c7641a27e5.png)



![image](https://user-images.githubusercontent.com/36288975/174224728-daf998f2-8ca4-44b8-828d-a3229688cf1e.png)


### PROCEDURE:
1.	Connect the circuit as per the circuit diagram 
2.	Connect the board to your computer via the USB cable.
3.	If needed, install the drivers.
4.	Launch the Arduino IDE.
5.	Select the board (If you the board is arduino uno, select accordingly).
6.	Select your serial port, accordingly ( E.g. COM5 )
7.	Open the file of the program  and verify the error , clear if any errors that are existing 
8.	Upload the program and check for the physical working. 
9.	Ensure safety before powering up the device 
10.	Plot the graph for the output voltage vs the resistance 


### PROGRAM 
```C

#include <AFMotor.h>

AF_DCMotor motor(4);// number of motor connected with shield

void setup() {
  Serial.begin(9600);           // set up Serial library at 9600 bps
  Serial.println("Motor test!");

  // turn on motor
  motor.setSpeed(200);
 
  motor.run(RELEASE);
}

void loop() {
  uint8_t i;
  
  Serial.print("tick");
  
  motor.run(FORWARD);
  for (i=0; i<255; i++) {
    motor.setSpeed(i);  
    delay(10);
 }
 
  for (i=255; i!=0; i--) {
    motor.setSpeed(i);  
    delay(10);
 }
  
  Serial.print("tock");

  motor.run(BACKWARD);
  for (i=0; i<255; i++) {
    motor.setSpeed(i);  
    delay(10);
 }
 
  for (i=255; i!=0; i--) {
    motor.setSpeed(i);  
    delay(10);
 }
  

  Serial.print("tech");
  motor.run(RELEASE);
  delay(1000);
}
```
 
 ## Simulation:
 
 ![1](https://user-images.githubusercontent.com/74660507/174421043-1eae7f42-a68e-4352-997f-1ab8834897d7.jpeg)

![2](https://user-images.githubusercontent.com/74660507/174421046-f0a3f174-f1bf-453f-8683-511f7a131b68.jpeg)

![3](https://user-images.githubusercontent.com/74660507/174421056-1d8a1ed2-857f-49a9-a1ed-38c8b3b8ee4a.jpeg)

 
### RESULTS : Arduino uno is interfaced with FSR and output values are indicated on a graph.
