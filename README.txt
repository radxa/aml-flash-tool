Hi,

This is the flash-tool for Amlogic platforms.
This aml-flash-tool script rely on update linux tool that need firstly to be installed.
Please read the file tools/_install_/README before to proceed here.

After than you can call aml-flash-tool.sh from anywhere, it will give you quick help :

Usage      : aml-flash-tool.sh path/to/aml_upgrade_package.img

Before to enter in the details here, let's explain how the connection work with the Amlogic board.

First you neeed to connect the board to your linux pc with a usb cable.
It can be done using a cable (USB Type A to USB Type A) or (USB Type A to USB Micro-B 5 pin).
It depends how the board has been designed actually.

The port to be used on the board is also dependant of the hardware. But you have to know that one particular USB 
port will be configured in slave mode at boot stage in two cases :

1/ No valid boot image can be found to boot on it, the Soc goes directly in usb boot mode
2/ USB boot mode forced in current u-boot flashed with the 'update' command.

When the Soc is in USB mode, if you have installed properly the update binary tool, your linux machine
should detect a new usb device called /dev/worldcup

By calling dmesg, you should see something like :

[19519.971862] usb 3-3.2: USB disconnect, device number 28
[40055.121229] usb 3-3.2: new high-speed USB device number 29 using xhci_hcd
[40055.212495] usb 3-3.2: New USB device found, idVendor=1b8e, idProduct=c003
[40055.212498] usb 3-3.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0

It's important to see this before to proceed on the next step, otherwise it will not work.

If all is here, it means you are now ready to flash the board or/and to control it from your PC machine

If you have already built android tree or linux tree, you can directly flash you new images by doing this : 

$ aml-flash-tool.sh path/to/aml_upgrade_package.img

It will flash all elements that are part of the aml_upgrade_package.img

Enjoy!

Marco (c) Amlogic
