# tej3m-2-07-python

#Jasper MacNeil

import time
import board
import adafruit_hcsr04
from adafruit_motor import servo
import pwmio


sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.GP12, echo_pin=board.GP13)
pwm = pwmio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50)
my_servo = servo.Servo(pwm)
DISTANCE_THRESHOLD = 50

while True:
    
    if (sonar.distance < DISTANCE_THRESHOLD):
        for angle in range(0, 180, 5):  
                my_servo.angle = angle
                time.sleep(0.05)
    else:
        for angle in range(180, 0, -5): 
                my_servo.angle = angle
                time.sleep(0.05)
    print ((sonar.distance))

