# RPi_donkeycar
Board: Raspberry Pi 3 Model B+

OS: Raspbian GNU/Linux 10 (buster) 

<img src="https://github.com/cly1213/RPi_donkeycar/blob/main/mycar/resultdemo.gif"/>

### Using PS3 Controller
<img src="https://github.com/cly1213/RPi_donkeycar/blob/main/mycar/ps3_white.png"/>
Plug in the PS3 with USB cable. Hit center PS logo button. Get and build the command line pairing tool. Run it:

```bash
wget http://www.pabr.org/sixlinux/sixpair.c
gcc -o sixpair sixpair.c -lusb
sudo ./sixpair
```

Use bluetoothctl to pair
```bash
(env) pi@raspberrypi:~ $ bluetoothctl
Agent registered
[bluetooth]# agent on
Agent is already registered
[bluetooth]# devices
Device 08:38:58:5C:63:25 Sony PLAYSTATION(R)3 Controller
[bluetooth]# trust 08:38:58:5C:63:25
Changing 08:38:58:5C:63:25 trust succeeded
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# quit
```

Unplug USB cable. Hit center PS logo button.

To test that the Bluetooth PS3 remote is working, verify that /dev/input/js0 exists.

```bash
(env) pi@raspberrypi:~ $ ls /dev/input/js0
/dev/input/js0
```
Ref: https://docs.donkeycar.com/index.html

