# **Cleanroom Monitoring System Setup**

## **Installing required packages**

First, run the standard updates:

    sudo apt update
    sudo apt full-upgrade
    sudo reboot

After the Pi has rebooted, install Python 3:

    sudo apt install python3

Next install the libraries:

    sudo pip3 install --upgrade setuptools
    pip3 install adafruit-circuitpython-dht
    pip3 install adafruit-circuitpython-ms8607
    pip3 install adafruit-circuitpython-pm25
    pip3 install adafruit-circuitpython_sgp30

## **Activating I2C ports**

The following information was taken from: https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup/configuring-i2c

To use sensors that require I2C ports (MS8607, PM25, and SGP30), you must configure the I2C. In the terminal:

    sudo apt-get install -y python-smbus
    sudo apt-get install -y i2c-tools
    sudo raspi-config
    
Go to Interfacing Options (On older versions, look under Advanced). Then go to I2C.

> Would you like the ARM I2C interface to be enabled? Yes

> Would you like the I2C kernel module to be loaded by default? Yes
                
Next, reboot the Pi:
    
    sudo reboot
    
After the Pi has rebooted, make sure the connected I2C devices are recognized:

    sudo i2cdetect -y 1

You should see one or more I2C addresses in use depending on the number of connected devices.
