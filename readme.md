# Surface Pro 5 Auto Screen Rotate Script

Tested on Linux Mint 21.3

This is a drop-in solution for enabling automatic screen rotation when running Linux on a Surface Pro 5. The Python script reads the accelerometer and flips the screen + reorients the touch screen when a new orientation is detected.

## Requires:

python, xorg-xinput, iio-sensor-proxy, inotify-tools, xrandr

# Setup:

1. Open GNOME Display Settings and turn on automatic screen rotation

2. Place the Python script in a convenient location (/opt is ok). You will need to set it to run at startup in the background. Here are some suggested methods (I used the cron job):

## Cron Job:
You can use a cron job to run your script at every reboot. Open the crontab with the command crontab -e and add the following line:

@reboot /usr/bin/python /path/to/your_script.py &

The & at the end ensures that the script runs in the background.

## rc.local:
Another method is to use the rc.local file. Edit the file with sudo nano /etc/rc.local and add the following line before the exit 0 line:

/usr/bin/python /path/to/your_script.py &

Again, the & will run your script in the background.

## Systemd Service:
You can create a systemd service file for your script. Follow this format:

[Unit]
Description=My Python Script Service
After=network.target

[Service]
ExecStart=/usr/bin/python /path/to/your_script.py
Type=simple
User=username
Group=groupname
Restart=on-failure

[Install]
WantedBy=multi-user.target

Save this file as /etc/systemd/system/myscript.service. Then enable and start your service with:

sudo systemctl enable myscript
sudo systemctl start myscript

This will set the script to run at every boot.

## nohup Command:
You can also use the nohup command to run your script in the background and ensure it continues running even if the terminal is closed:

nohup /usr/bin/python /path/to/your_script.py &

Don't forget to make your script executable with chmod +x /path/to/your_script.py.
