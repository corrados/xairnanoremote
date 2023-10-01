# Python script to control a Behringer XAIR mixer with a Korg nanoKONTROL connected to a Raspberry Pi

The Python script [xairremote.py](xairremote.py) implements the connection between the Korg nanoKONTROL MIDI mixer with
a Behringer X-AIR or X32 digital mixer. The nanoKONTROL is connected to a Raspberry Pi (e.g. a Raspberry Pi Zero W)
using USB and the connection from the Raspberry Pi to the Behringer mixer is either via wireless LAN (WiFi) or
an Ethernet cable. The protocol used to talk to the Behringer mixer is OSC (using the library [python-x32](https://github.com/tjoracoder/python-x32)).

You can see the script in action in this [Youtube video](https://youtu.be/CBD8GMQ4UX4).


## Setup Raspberry Pi

Use the following commands to setup the Raspberry Pi and start the script:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install git python3-pip
python3 -m pip install alsa-midi
git clone https://github.com/corrados/xairnanoremote.git
cd xairnanoremote
git submodule update --init
python3 xairremote.py
```

Optionally, insert the following line in rc.local to auto start the script on boot up of the
Raspberry Pi:

```
su pi -c 'cd /home/pi/xairnanoremote;sleep 15;python3 xairremote.py' &
```


## Debugging with X32 emulator by pmaillot

I have used an X32 emulator software by pmaillot to create the Python script. To compile and run
the emulator, you can use the following commands:

```
cd X32-Behringer
make
make X32
cd build
./X32 -i127.0.0.1
```

