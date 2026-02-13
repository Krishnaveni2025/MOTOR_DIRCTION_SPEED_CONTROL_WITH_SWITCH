# MOTOR_DIRCTION_SPEED_CONTROL_WITH_SWITCH
Alright Krishnaveni 🌸, let’s break down your **motor control milestones** into clear implementation steps so you can code and test them one by one.

---

## 🔹 Milestone 1: Motor Speed Control with PWM
**Goal:** Generate a 1 kHz PWM signal on pin **P1.2** with 25% duty cycle, connect it to the EN pin of the motor driver, and use GPIO pins for IN1/IN2.

1. **PWM Configuration**
   - Configure **Timer/Counter/PWM module** for 1 kHz frequency.
   - Duty cycle = 25% (compare value = 25% of period).
   - Route PWM output to **P1.2**.

2. **GPIO Setup**
   - Configure **IN1** and **IN2** as digital outputs.
   - Example: IN1 = 1, IN2 = 0 → forward rotation.

3. **Test**
   - Motor should rotate at ~25% speed.
   - Change duty cycle manually to verify speed scaling.

---

## 🔹 Milestone 2: Direction Control with GPIO Interrupt
**Goal:** Use switch on **P3.7** to toggle direction with debouncing.

1. **Interrupt Setup**
   - Configure **P3.7** as input with interrupt on rising edge.
   - Enable Port 3 interrupt in NVIC.

2. **Debouncing**
   - Inside ISR, disable further interrupts.
   - Add software delay (~50–100 ms).
   - Re‑enable interrupts after delay.

3. **Direction Change Logic**
   - On valid press:
     - Halt motor: IN1 = 0, IN2 = 0.
     - Delay (e.g., 500 ms).
     - Toggle direction: if last was forward (IN1=1, IN2=0), switch to reverse (IN1=0, IN2=1).

---

## 🔹 Duty Cycle Adjustment
**Goal:** Cycle duty cycle in increments of 25% → 25 → 50 → 75 → 100 → back to 25.

- Maintain a **global variable** `dutyCycleIndex` (values 0–3).
- Each valid switch press:
  - Increment index.
  - Compute duty cycle = (index+1) * 25%.
  - Update PWM compare register.
- Wrap around after 100% back to 25%.

---




Would you like me to now **expand this pseudocode into actual C code for PSoC Creator APIs** (with `PWM_Start()`, `PWM_WriteCompare()`, `CyDelay()` etc.), so you can directly compile and test it?

