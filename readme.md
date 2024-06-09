# Surface Pro 5 Auto Screen Rotate Script

Tested on Linux Mint 21.3

Reads the accelerometer and flips the screen + reorients the touch screen when a new orientation is detected. Shell script + desktop file allow for it to be toggled from most start menus

## Requires:

python, xorg-xinput, iio-sensor-proxy, inotify-tools, xrandr

# Setup:

Open GNOME Display Settings and turn on automatic screen rotation

Run `sudo systemctl start iio-sensor-proxy` before you try to run the script. it won't work without that.

Then, you have a few options for running it. You can either run `python rotate.py` directly, or you can run `./rotate.sh install` to copy the needed files to get the desktop icon toggle working.
