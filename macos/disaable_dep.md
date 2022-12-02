# Disable Device Enrollment Program (DEP) notification

[Source](https://gist.github.com/henrik242/65d26a7deca30bdb9828e183809690bd)

NB! `CMD+R` is replaced with holding the power button on M1 macs.

## With full reinstall (recommended)

1. Boot into recovery using `CMD+R` during reboot, wipe the harddrive using Disk Utility, and select reinstall macOS

2. Initial installation will run for approximately 1 hour, and reboot once

3. It will then show a remaining time of about 10-15 minutes

4. When it reboots again, be sure to press `CMD+R` to boot into recovery and continue with **Main procedure**

## Without full reinstall

Boot to Recovery Mode by holding `CMD+R` during restart and continue with **Main procedure**

## Main procedure

1. Open Utilities → Terminal and type

    ```bash
    csrutil disable
    reboot
    ```

2. Hold `CMD+R` during the reboot to enter Recovery Mode again

3. Enter Disk Utility, and mount the `Macintosh HD` volume (or whatever your main volume is named).  (It might already be mounted.)

4. Exit Disk Utility, open Utilities → Terminal, and type

    ```bash
    cd "/Volumes/Macintosh HD/System/Library"
    cd ../../etc
    echo "0.0.0.0 iprofiles.apple.com" >> hosts
    echo "0.0.0.0 mdmenrollment.apple.com" >> hosts
    echo "0.0.0.0 deviceenrollment.apple.com" >> hosts
    echo "0.0.0.0 gdmf.apple.com" >> hosts
    csrutil enable
    reboot
    ```

5. If you come to the “Choose your country/location” dialogue, make sure to not select a wireless network, but “continue without an internet connection”

6. After a normal boot, you can verify the DEP status in Terminal:

    ```bash
    profiles status -type enrollment

    Enrolled via DEP: No
    MDM enrollment: No
    ```
