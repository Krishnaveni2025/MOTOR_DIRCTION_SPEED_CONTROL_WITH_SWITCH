# MOTOR_DIRCTION_SPEED_CONTROL_WITH_SWITCH
GOAL: Change motor rotation direction and RPM (motor speed) on press of a switch
Mileston 1: Implement Motor speed control using pwm signal
              configure the pwm output on pin P1.2 to generate a 1KHz signal with a duty cycle of 25%.
              connect the pwm signal to the EN pin of the motor driver. Additionally, use two GPIO pins to control IN1 and IN2 and demonstrate that motor is rotating
Milestone 2: Implement direction control of motor with GPIO Interrupt (toggle switch)
             configure a GPIO switch on pin P3.7 to trigger a port 3 interrupt whenever the sw1 switch is pressed. Implement debouncing to ensure reliable operation.
             once a genuine key press is detected, HALT the motor by driving IN1 = IN2 = 0 and wait for reasonable amount of time using software delays
                  (use your judgement to decide what constitutes reasonable time)
             change the motor's direction after the delay elapses
             Ensures that the pwm duty cycle is adjusted in increments of 25% aas the following:
             25%-->50%-->75%-->100%-->25%-->......
