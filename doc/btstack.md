Using InternalBlue with BTstack
===============================

Instead of using the native Bluetooth Host Stack, InternalBlue can also be used with
the user-space [BTstack](https://bluekitchen.github.com/btstack) Bluetooth Stack
over a TCP/IP socket.

BTstack runs on most desktop operating systems (macOS, Linux, FreeBSD, Windows) and
supports most Bluetooth Controllers incl. Broadcom/Cypress/Infineon over H4/UART as
well as H2/USB.

Setup of BTstack Daemon
-----------------------

Clone the BTstack repository and change into `port/daemon`. Follow the readme.md and
configure the daemon for USB (libusb or WinUSB) with `--with-tranport=usb` for USB
or H4/UART with `--with-transport=h4 --with-uart-device=Your_UART_Device`.

Before starting an InternalBlue example, start the BTstack Daemon with `src/BTstackDaemon --tcp`.

Usage
-----

To use the BTstack Daemon as InternalBlue transport, please create an instance of `BTstackCore`.

HCI Traces
----------
The BTstack Daemon write an HCI trace in Apple's PacketLogger format to `/tmp/hci_dump.pklg` 
(most systems) or `hci_dump.pklg` (Windows). 

Host Stack
----------

In addition to the low-level features of InternalBlue, common Bluetooth Host functionality
can be triggered via the socket connection to the BTstack Daemon. 
For more information on how to control the BTstack Daemon, please ask on the
[BTstack Google Group](https://groups.google.com/group/btstack-dev).
