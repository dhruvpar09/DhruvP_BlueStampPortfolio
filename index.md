# Self Driving Car
This Arduino Uno-based autonomous vehicle uses infrared- and ultrasonic-based sensors for short and long range object detection, respectively. Using the data from these sensors, it adjusts its preexisting motion to avoid these obstacles. I am tentatively considering adding a camera to this robot and incorporating image recognition technologies, although this may change if time constraints or other factors do not permit it.

```HTML
You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions. 
(this isn't commented out to keep it visible. it should be deleted before the website is complete.)
```

| **Student** | **School** | **Areas of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Dhruv P | Stratford Preparatory | Robotics | Incoming Junior
| | Blackford | Computer Science | 

**Replace the BlueStamp logo below with an image of yourself and your completed project. (note to self: this image is a placeholder for now.) Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](SunFounderArduinoSelfDrivingCarImage.png)
  <!--
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/aaaaaaaaa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/bbbbbb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 
-->

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/FzxPjumBy4o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

  My summer intensive project is the self driving car. I chose this project because it integrates sensors and motor movement into one project. Most robots in the industry need to change their motion as a reaction to sensor inputs; a project that does just that gives me valuable experience to build on in future robotics projects. This project also has the flexibility to support many potential modifications, giving me many options to expand on it depending on which technologies I choose to gain experience with.

  I decided that constructing the self-driving car's hardware would be my first milestone. Since my main project required three milestones, and software development for this project can be separated into two milestones, (motors and sensors) completing the hardware appeared to be a sensible first milestone for this project. To complete this milestone, I attached the Arduino Uno, two motors, three wheels, a battery, a breadboard, and various sensors to the base plate of the car. In order to test the motors to make sure they worked properly, I connected the motors and the motor driver to the Arduino Uno. It turns out that the motors only rotated when their corresponding motor driver pins were connected to the ground, not to pins that source current. This surprised me, since I assumed these motor control pins were providing power to the motors instead of solely instructing the motor driver on how to control them. However, I managed to adjust to this information, using the Arduino's INPUT and OUTPUT LOW modes to toggle whether each motor was rotating or not. I wrote some tester code to ensure that the motors could operate properly once they were programmed, and after the motors passed these tests, I decided to film my first milestone video. 

Motor Tester Code:
```c++

//methods to either stop each motor or move them forward or backward
void leftMotorBackward() {
  pinMode(leftBackwardPin, INPUT);
  pinMode(leftForwardPin, OUTPUT);
  digitalWrite(leftForwardPin, LOW);
}

void leftMotorForward() {
  pinMode(leftForwardPin, INPUT);
  pinMode(leftBackwardPin, OUTPUT);
  digitalWrite(leftBackwardPin, LOW);
}

void leftMotorStop() {
  pinMode(leftForwardPin, INPUT);
  pinMode(leftBackwardPin, INPUT);
}

void rightMotorBackward() {
  pinMode(rightBackwardPin, INPUT);
  pinMode(rightForwardPin, OUTPUT);
  digitalWrite(rightForwardPin, LOW);
}

void rightMotorForward() {
  pinMode(rightForwardPin, INPUT);
  pinMode(rightBackwardPin, OUTPUT);
  digitalWrite(rightBackwardPin, LOW);
}

void rightMotorStop() {
  pinMode(rightBackwardPin, INPUT);
  pinMode(rightForwardPin, INPUT);
}

//setting some constants as the pin numbers of the motors
int rightBackwardPin = 2;
int rightForwardPin = 4;
int leftForwardPin = 7;
int leftBackwardPin = 8;

//Arduino-required setup function
void setup(){
  Serial.begin(9600);
  Serial.println("program started");

  //set pins to input so that they are by default stopping motor rotation when the code starts
  pinMode(rightBackwardPin, INPUT);
  pinMode(rightForwardPin, INPUT);
  pinMode(leftForwardPin, INPUT);
  pinMode(leftBackwardPin, INPUT);

  //setting the pins to low current output
  //when they are set to output mode, this will prevent them from damaging the motor driver
  //which would happen from a current supply that the motor driver could not handle
  digitalWrite(rightBackwardPin, LOW);
  digitalWrite(rightForwardPin, LOW);
  digitalWrite(leftForwardPin, LOW);
  digitalWrite(leftBackwardPin, LOW);
}

//change this constant to change the speed at which the tester code runs
int timeConst = 1000;

//arduino-required loop function
void loop(){
  rightMotorStop();
  leftMotorStop();
  delay(2 * timeConst);

  //test the right motor's forward motion, backward motion, and stopping ability
  rightMotorForward();
  delay(1 * timeConst);
  rightMotorStop();
  delay(1 * timeConst);
  rightMotorBackward();
  delay(1 * timeConst);
  rightMotorStop();
  delay(1 * timeConst);

  //pause
  delay(2 * timeConst);

  //test the left motor's forward motion, backward motion, and stopping ability
  leftMotorForward();
  delay(1 * timeConst);
  leftMotorStop();
  delay(1 * timeConst);
  leftMotorBackward();
  delay(1 * timeConst);
  leftMotorStop();
  delay(1 * timeConst);

  //pause
  delay(2 * timeConst);
}

```

<!--
For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project
-->

# Starter Project
## Retro Arcade Console
<iframe width="560" height="315" src="https://www.youtube.com/embed/6TELPC9OSp4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My starter project of choice was the Retro Arcade Console. This console simulates multiple retro video games via a CPU soldered onto its motherboard. When the user presses one of the six buttons on the console, (excluding the on/off button) the CPU identifies the button that has been pressed, and then determines how to change the game environment accordingly. It then instructs the LCD screens to display different shapes in order to reflect this change.

<!--
# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:
  Serial.thisIsPlaceHolderCode();
}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
-->
