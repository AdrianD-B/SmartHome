# SmartHome Captsone Project Blog

## Week 10 pcb soldered and functioning
All works accordingly except for the buzzer which does work but is very weak sounding. Pretty sure i broke the buzzer since i did a test with same resistance and it still became lower than usual.

![IMG_20191207_215312768](https://user-images.githubusercontent.com/54862231/70383545-b050b480-193d-11ea-9e81-566d23c7aded.jpg)

![IMG_20191207_215111436](https://user-images.githubusercontent.com/54862231/70383582-26edb200-193e-11ea-8a1f-a55b292656c7.jpg)

## Week 9 pcb complete
pcb part failed since the componnent needs to be soldered from the bottom meaning that the connections are flipped:

![image](https://user-images.githubusercontent.com/54862231/70078917-a93e4500-15d1-11ea-841b-06c10aaba2a9.png)

new gerber file and breadboard design file:

![image](https://user-images.githubusercontent.com/54862231/70086254-fb866280-15df-11ea-9747-9ca9253ebba7.png)

![image](https://user-images.githubusercontent.com/54862231/70086292-12c55000-15e0-11ea-85b6-22c55b001d99.png)



## Week 8 breadboarding complete and code
breadboard complete:
![image](https://user-images.githubusercontent.com/54862231/70077583-0edd0200-15cf-11ea-9273-255e69d3c73c.png)

arduino code:
//TMP36 Pin Variables
int sensorPin = PA0; //the analog pin the TMP36's Vout (sense) pin is connected to
                        //the resolution is 10 mV / degree centigrade with a
                        //500 mV offset to allow for negative temperatures
float temperature = 0;
 
/*
 * setup() - this function runs once when you turn your Arduino on
 * We initialize the serial connection with the computer
 */
void setup()
{
  Serial.begin(9600);  //Start the serial connection with the computer
                       //to view the result open the serial monitor
  pinMode(PA1,OUTPUT);
}
 
void loop()                     // run over and over again
{
 //getting the voltage reading from the temperature sensor
 int reading = analogRead(sensorPin);  
 
 // converting that reading to voltage, for 3.3v arduino use 3.3
 float voltage = reading * 5.0;
 voltage /= 1023.0;
 
 // print out the voltage
 Serial.print(voltage); Serial.println(" volts");
 
 // now print out the temperature
 int temperatureC = map(reading,205,1023,-500,1500);  //converting from 10 mv per degree wit 500 mV offset
 temperature = temperatureC/10.0;//to degrees ((voltage - 500mV) times 100)
 
 Serial.print(temperature); Serial.println(" degrees F");
 
 // now convert to Fahrenheit
 //float temperatureF = (temperatureC * 9.0 / 5.0) + 32.0;
 //Serial.print(temperatureF); Serial.println(" degrees F");

 if (temperature > 75){
  analogWrite(PA1,HIGH);
  delay(1000);
  analogWrite(PA1,LOW);
  delay(1000);
 }
 delay(1000);                                     //waiting a second
}

arduino output (higher than 75 in this example rings the buzzer and lower than 75 will shutoff the buzzer)
![image](https://user-images.githubusercontent.com/54862231/70077868-a3476480-15cf-11ea-97ed-3275525aa89f.png)


## Week 7 Breadboard and PCB design
Gerber viewer:

![Default](https://user-images.githubusercontent.com/54862231/67780192-19d6cc80-fa3c-11e9-80d7-9fbb309de1cd.png)

Breadboard: 

![Screenshot_2](https://user-images.githubusercontent.com/54862231/67780337-5acee100-fa3c-11e9-8cd3-b3541d048885.png)

Schematic:

![Screenshot_1](https://user-images.githubusercontent.com/54862231/67780514-910c6080-fa3c-11e9-9a91-516aea3c226a.png)

## Week 4 Budget

![Screenshot_3](https://user-images.githubusercontent.com/54862231/67780749-eba5bc80-fa3c-11e9-9051-c0d799068fd1.png)

## Week 3 Schedule
sources:

[https://www.youtube.com/watch?v=ZKj12hfqrZQ](https://www.youtube.com/watch?v=ZKj12hfqrZQ)


