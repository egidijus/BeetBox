BeetBox
=======

This is probably not especially useful to anyone, but may be interesting to those curious about the inner workings of the [Beetbox](http://scott.j38.net/interactive/beetbox/).
The code for interfacing with the MPR121 is based on [an Arduino example by Jim Lindblom](http://bildr.org/2011/05/mpr121_arduino/).

These are the things you need to install before you get cooking.
I am assuming you are using ubuntu/raspbian.

	apt-get install i2c-tools python-smbus htop python-dev python-rpi.gpios python-pygame

Enable the MPR121 via GPIO + i2c-tools:

	sudo nano /etc/modules
	
Add this:

	i2c-bcm2708
	i2c-dev

Remove from black list i2c:

	sudo nano /etc/modprobe.d/raspi-blacklist.conf
	
Comment out like this:

	#blacklist spi-bcm2708
	#blacklist i2c-bcm2708


Try to detect MPR121 once connected:

	sudo i2cdetect -y 1

Caveats:
 - The sound will go crappy after about 9 hours - this is because the DAC is not always on, and there are some processing issues.
 - Here is a proper explanation and how to get audiophile sound output.
 - http://www.luke.maurits.id.au/blog/post/getting-nice-sound-from-the-raspberry-pi.html
 - http://www.behringer.com/EN/Products/UCA202.aspx
 - http://volumio.org/raspberry-pi-i2s-dac-sounds-so-good/
 - http://www.raspyfi.com/the-right-usb-dac-for-your-raspberry-pi/
 - http://www.hifiberry.com/dac
