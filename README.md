# Simple MOFSET solution to have a PWM solution using a standard 2 pins ventilator on a raspberry pi.

This implements Andreas Spiess' article and python code (http://www.sensorsiot.org/variable-speed-cooling-fan-for-raspberry-pi-using-pwm-video138/).
I have simply removed the battery related code (unused), add a systemd service to start the program at boot at log the last output information (details as log and the fan speed % value).

## Hardware

Components:
- MOFSET IRLZ44n
- R1 1K ohms
- R2: 470 ohms
- Flyback diode 1N4001
- 5V 2 pins fan

Wire chart: ![Wiring diagram](electronic_diagram.jpg)

## Software

I've just modified the following stuffs on the python script:
- remove all battery-related code (unused)
- new log file for the debug and fan speed output, so I can read them with a LUA script in Domoticz

I've also added a new simple systemd service.

Setup:
```
cd /home/pi
git clone <THIS REPO> pwm_fan
cd pwm_fan
chmod 755 /home/pi/pwm_fan/pwm_mofset_GPIO_17.service
sudo ln -s /home/pi/pwm_fan/pwm_mofset_GPIO_17.service /etc/systemd/system/pwm_mofset_GPIO_17.service
sudo systemctl daemon-reload
sudo systemctl start pwm_mofset_GPIO_17
sudo systemctl status -a pwm_mofset_GPIO_17
sudo systemctl enable pwm_mofset_GPIO_17
```
Logs:
```
$ cat /var/log/pwm_mofset_GPIO_17.log
actualTemp 46.00 TempDiff 1.00 pDiff 15.00 iDiff 10.40 fanSpeed    25

$ cat /var/log/pwm_mofset_GPIO_17.rpm
25
```
