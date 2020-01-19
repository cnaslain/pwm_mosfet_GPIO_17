# Simple MOFSET solution to have a PWM solution using a standard 2 pins ventilator on a raspberry pi.

This implements Andreas Spiess' article and python code (http://www.sensorsiot.org/variable-speed-cooling-fan-for-raspberry-pi-using-pwm-video138/).
I have simply removed the battery stuffs (unused) and add a systemd service?

Hardware components:
- MOFSET IRLZ44n
- R1 1K ohms
- R2: 470 ohms
- Flyback diode 1N400X
- 5V 2 pins ventilator

