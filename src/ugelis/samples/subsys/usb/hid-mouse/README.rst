.. _usb_hid-mouse:

USB HID mouse Sample Application
####################################

Overview
********

This sample app demonstrates use of a USB Human Interface Device (HID) driver
by the uGelis project.  This very simple driver enumerates a board with a button
into a "mouse" that only has a left-mouse button and can't move.
This sample can be found under :file:`samples/subsys/usb/hid-mouse` in the
uGelis project tree.

Requirements
************

This project requires an USB device driver, and there must has at least one
GPIO button in your board.

To use this sample, you will require a board that defines the user switch in its
header file. The :file:`board.h` must define the following variables:

- SW0_GPIO_NAME
- SW0_GPIO_PIN

Building and Running
********************

This sample can be built for multiple boards, in this example we will build it
for the nucleo_f070rb board:

.. ugelis-app-commands::
   :ugelis-app: samples/subsys/usb/hid-mouse
   :board: nucleo_f070rb
   :goals: build
   :compact:

After you have built and flashed the sample app image to your board, plug the
board into a host device, for example, a PC running Linux.
The board will be detected as shown by the Linux dmesg command:

.. code-block:: console

    dmesg | tail -10
    usb 2-2: new full-speed USB device number 2 using at91_ohci
    usb 2-2: New USB device found, idVendor=2fe3, idProduct=0100
    usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
    usb 2-2: Product: uGelis HID mouse sample
    usb 2-2: Manufacturer: UGELIS
    usb 2-2: SerialNumber: 0.01
    input: UGELIS uGelis HID mouse sample as /devices/soc0/ahb/600000.ohci/usb2/2-2/2-2:1.0/0003:2FE3:0100.0001/input/input0
    hid-generic 0003:2FE3:0100.0001: input: USB HID v1.10 Mouse [UGELIS uGelis HID mouse sample] on usb-at91-2/input0

You can also monitor mouse events by using the standard Linux ``evtest`` command
(see the `Ubuntu evtest man page`_ for more information about this tool):

.. _Ubuntu evtest man page:
   http://manpages.ubuntu.com/manpages/trusty/man1/evtest.1.html

.. code-block:: console

    sudo evtest /dev/input/event0
    Input driver version is 1.0.1
    Input device ID: bus 0x3 vendor 0x2fe3 product 0x100 version 0x110
    Input device name: "UGELIS USB-DEV"
    Supported events:
      Event type 0 (EV_SYN)
      Event type 1 (EV_KEY)
        Event code 272 (BTN_LEFT)
        Event code 273 (BTN_RIGHT)
        Event code 274 (BTN_MIDDLE)
      Event type 2 (EV_REL)
        Event code 0 (REL_X)
        Event code 1 (REL_Y)
        Event code 8 (REL_WHEEL)
      Event type 4 (EV_MSC)
        Event code 4 (MSC_SCAN)
    Properties:
    Testing ... (interrupt to exit)

When you press the button on your board, it will act as if the left
mouse button was pressed, and this information will be displayed
by ``evtest``:

.. code-block:: console

    Event: time 1167609663.618515, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
    Event: time 1167609663.618515, type 1 (EV_KEY), code 272 (BTN_LEFT), value 1
    Event: time 1167609663.618515, -------------- SYN_REPORT ------------
    Event: time 1167609663.730510, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001
    Event: time 1167609663.730510, type 1 (EV_KEY), code 272 (BTN_LEFT), value 0
    Event: time 1167609663.730510, -------------- SYN_REPORT ------------
