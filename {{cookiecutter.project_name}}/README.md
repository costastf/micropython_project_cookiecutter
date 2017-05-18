# {{ cookiecutter.project_name }}
{{ cookiecutter.project_short_description}}

Some electrical assembly required :)

# WARNING
Only mess with **high** current if you really really know what you are doing. If
not certified to do so please refrain from it. It can definitely kill you,
which is not a desired outcome for any hobby project.


# Problem statement


# Solution


# Requirements


# Physical Connection

You can see pictures of the connectivity under the images directory [here](images)


# Schematics

Images in png format and a fritzing project can be found under [schematics](schematics)


# Configuration

 Rename configuration_sample.json to configuration.json and edit accordingly.
  Everything else should just work out of the box.


# Flashing micropython

Required tools:

   [esptool](https://github.com/espressif/esptool) (Follow installation instructions)

  With the board connected to a usb port of your linux box assuming that the
  port is ttyUSB0 (check with dmesg after connecting to see what is assigned)

    esptool.py --port /dev/ttyUSB0 erase_flash
    esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0 MICROPYTHON_FIRMWARE_FOR_ESP8266.bin

  I have had some wemos d1 mini boards having trouble flashing with the above with
  garbage on the serial and the led staying on. On those boards this command
  works.

    esptool.py --port /dev/ttyUSB0 write_flash -fm dio -fs 32m 0 MICROPYTHON_FIRMWARE_FOR_ESP8266.bin


# Loading the project

Required tools:

   [ampy](https://github.com/adafruit/ampy) (Follow installation instructions)

    export AMPY_PORT=/dev/ttyUSB0
    for file in `ls project`
        do
            ampy put $file
        done


# Checking output