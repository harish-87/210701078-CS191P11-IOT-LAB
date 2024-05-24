Intelli-View Glass is an innovative project aimed at revolutionizing privacy and comfort in architectural design. By integrating cutting-edge smart blind technology with traditional glass surfaces, this project offers a dynamic solution for controlling light, visibility, and thermal comfort within indoor spaces. The core technology leverages sensors and intelligent algorithms to automatically adjust the opacity of the glass, providing users with seamless control over their environment. Through real-time monitoring of external factors such as sunlight intensity, temperature, and user preferences, Intelli-View Glass optimizes natural light utilization while minimizing glare and heat gain. Furthermore, its intuitive interface allows users to customize settings and schedules, enhancing energy efficiency and personalizing the indoor experience. 
HARDWARE SPECIFICATIONS FOR APPLICATION  
 
Processor:Pentium IV Or Higher 
Memory Size:256 GB (Minimum) 
HDD:40 GB (Minimum)  
 
SOFTWARE SPECIFICATIONS  
Application:ARDUINO NANO 
 
HARDWARE COMPONENTS FOR PROTOTYPE  
Sensor : Hc-SR04 Ultrasonic sensor  Board        :
Aurdino pro mini                     
Battery 
Speaker 
Ultrasonic glasses 




  CODE EXPLAINATION

  SETUP:
#define trigPin 8 and #define echoPin 7: These lines create symbolic names for the Arduino pins that will be connected to the ultrasonic sensor. trigPin will be connected to the trigger pin of the ultrasonic sensor, and echoPin will be connected to the echo pin.

#define buzzer 12: This line defines a symbolic name for the pin that will be connected to the buzzer.

void setup() { ... }: This is the setup function in Arduino code, which runs once when the Arduino is powered on or reset.

Serial.begin(9600);: This line initializes serial communication at a baud rate of 9600 bits per second. This is typically used for debugging purposes, allowing the Arduino to send data to a computer over a USB connection.

pinMode(trigPin, OUTPUT); and pinMode(echoPin, INPUT);: These lines set the pin modes for the trigPin and echoPin. trigPin is configured as an output, as it will send the trigger signal to the ultrasonic sensor. echoPin is configured as an input, as it will receive the echo signal from the sensor.

pinMode(buzzer, OUTPUT);: This line sets the pin mode for the buzzer pin. It configures it as an output, as the Arduino will be sending signals to the buzzer to control it.
LOOP:
long duration, distance;: This line declares two variables duration and distance of type long, which will be used to store the duration of the ultrasonic pulse and the calculated distance, respectively.

digitalWrite(trigPin, LOW);: This line sets the trigPin to a low state to ensure a clean pulse.

delayMicroseconds(2);: This line introduces a small delay of 2 microseconds.

digitalWrite(trigPin, HIGH);: This line sets the trigPin to a high state to trigger the ultrasonic sensor.

delayMicroseconds(10);: This line introduces a delay of 10 microseconds.

digitalWrite(trigPin, LOW);: This line sets the trigPin back to a low state to end the trigger pulse.

duration = pulseIn(echoPin, HIGH);: This line measures the duration of the pulse received on the echoPin when it goes from low to high. This duration represents the time taken by the ultrasonic pulse to travel to the object and back.

distance = (duration/2) / 29.1;: This line calculates the distance based on the duration of the pulse. The speed of sound is approximately 29.1 microseconds per centimeter. Since the pulse travels to the object and back, the distance is half of the total travel time.

Serial.print(distance);: This line prints the calculated distance to the serial monitor.

Serial.println(" cm");: This line prints "cm" to indicate the unit of distance.

if (distance > 30 and distance < 62) { tone(buzzer,100,50); }: If the distance is between 30 and 62 centimeters, an intermittent beep with a frequency of 100 Hz and a duration of 50 milliseconds is produced by the buzzer.

if (distance > 0 and distance < 31) { tone(buzzer,100); }: If the distance is less than 31 centimeters, a long solid beep with a frequency of 100 Hz is produced by the buzzer.

else { delay(500); }: If the distance is neither in the range of 30-62 nor less than 31 centimeters, a delay of 500 milliseconds is introduced.

