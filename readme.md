# Example for running a script on usb drive mount

Based off of <https://www.axllent.org/docs/view/auto-mounting-usb-storage/>

## Setup

(as root)

1. place `85-mount_test.rules` into `/etc/udev/rules.d/`
2. edit it so that line 12:
    - has your username (instead of `ftseng`)
    - has the path to the script you want to execute instead of `/tmp/example.sh` (see example script)
        - make sure your script has execute permissions (`chmod +x /tmp/example.sh`)
3. run `udevadm control --reload-rules` to reload the udev rules

## Example script

The example script `example.sh` uses the `notify-send` program to show a notification describing what path the USB was mounted to. In `85-mount_test.rules`, this path is passed as the only argument to `/tmp/example.sh` (the `/media/%E{dir_name}` part).
