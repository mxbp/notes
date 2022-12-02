# Create a MacOS ISO file from an Installer

TL;DR

Change `MacOS` to your OS (ex. Big\ Sur, Monterey, Ventura).

```bash
hdiutil create -o /tmp/`MacOS` -size 16g -volname BigSur -layout SPUD -fs HFS+J
hdiutil attach /tmp/`MacOS`.dmg -noverify -mountpoint /Volumes/`MacOS`
sudo /Applications/Install\ macOS\ `MacOS`.app/Contents/Resources/createinstallmedia \
    --volume /Volumes/BigSur --nointeraction
hdiutil eject -force  /Volumes/Install\ macOS\ `MacOS`
hdiutil convert /tmp/`MacOS`.dmg -format UDTO -o ~/Downloads/`MacOS`
mv -v ~/Downloads/`MacOS`.cdr ~/Downloads/`MacOS`.iso
sudo rm -fv /tmp/`MacOS`.dmg
```

## e.g. ISO Monterey Installer

```bash
$ hdiutil create -o /tmp/Monterey -size 16g -volname Monterey -layout SPUD -fs HFS+J

created: /tmp/Monterey.dmg

$ hdiutil attach /tmp/Monterey.dmg -noverify -mountpoint /Volumes/Monterey

/dev/disk3              Apple_partition_scheme         
/dev/disk3s1            Apple_partition_map            
/dev/disk3s2            Apple_HFS                       /Volumes/Monterey

$ sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia \
    --volume /Volumes/Monterey \
    --nointeraction

Erasing disk: 0%... 10%... 20%... 30%... 100%
Making disk bootable...
Copying to disk: 0%... 10%... 20%... 30%... 40%... 50%... 60%... 70%... 80%... 90%... 100%
Install media now available at "/Volumes/Install macOS Monterey"

$ hdiutil eject -force  /Volumes/Install\ macOS\ Monterey

"disk3" ejected.

$ hdiutil convert /tmp/Monterey.dmg -format UDTO -o ~/Downloads/Monterey

Reading Driver Descriptor Map (DDM : 0)…
Reading Apple (Apple_partition_map : 1)…
Reading  (Apple_Free : 2)…
Reading disk image (Apple_HFS : 3)…
.......................................................................................................................
....................................................................................
Elapsed Time: 27.966s
Speed: 585.8MB/s
Savings: 0.0%
created: /Users/User/Downloads/Monterey.cdr

$ mv ~/Downloads/Monterey.cdr ~/Downloads/Monterey.iso

/Users/User/Downloads/Monterey.cdr -> /Users/User/Downloads/Monterey.iso

$ sudo rm -fv /tmp/Monterey.dmg
```

## Issue

```bash
    Erasing Disk: 0%... 10%...
    Error erasing disk error number (22, 0)
    A error occurred erasing the disk.
```

## Resolve

The only workaround was to reboot my Mac and try again.
