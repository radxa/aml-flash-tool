# Amlogic flash tool

This is the flash-tool for Amlogic platforms.

----------------------------

## Support list

- Radxa Zero

## Installation

This aml-flash-tool script rely on update linux tool that need firstly to be installed.
Please run

```bash
./INSTALL
```

 to install dependency and usb rules.

After than you can call aml-flash-tool.sh from anywhere, it will give you quick help :

```bash
$ aml-flash-tool.sh
Missing img argument
Usage      : /usr/local/bin/aml-flash-tool.sh path/to/aml_upgrade_package.img
```

## Flash

### Run into mask rom mode

You should refer to Board indication to power up it into maskrom mode.

When the Soc is running in maskrom mode properly,  your linux machine should detect a new usb device

By calling dmesg, you should see something like :

```bash
[177122.811055] usb 1-2.2: new high-speed USB device number 31 using xhci_hcd
[177123.584038] usb 1-2.2: New USB device found, idVendor=1b8e, idProduct=c003, bcdDevice= 0.20
[177123.584044] usb 1-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[177123.584048] usb 1-2.2: Product: GX-CHIP
[177123.584051] usb 1-2.2: Manufacturer: Amlogic
```

And you will see a Amlogic usb device when you execute lsusb command.

```bash
$ lsusb
Bus 001 Device 052: ID 1b8e:c003 Amlogic, Inc. USB DEVICE
```

It's important to see this before to proceed on the next step, otherwise it will not work.

### Run flash command

If all is here, it means you are now ready to flash the board or/and to control it from your PC machine

If you have already built android tree or linux tree, you can directly flash you new images by doing this :

```bash
$ aml-flash-tool.sh path/to/aml_upgrade_package.img
```

It will flash all elements that are part of the aml_upgrade_package.img
