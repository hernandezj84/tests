or example, inside the container, you can add a custom udev rule file (e.g., /etc/udev/rules.d/99-android.rules) to allow non-root users to access Android devices. The rule might look something like this:

makefile
Copy code
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e11", MODE="0666"
This rule grants read/write permissions to any user for the device with idVendor=18d1 and idProduct=4e11 (which is a common Android USB device identifier). Be sure to adjust the idVendor and idProduct values according to your specific device.

After adding the udev rule, reload the udev configuration:

bash
Copy code
sudo udevadm control --reload-rules
