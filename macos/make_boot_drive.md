# Make a MacOS Installer USB Boot Drive

Change `MacOS` to your OS (ex. Big\ Sur, Monterey, Ventura) and change `UNTITLED` to your drive name

```bash
$ sudo /Applications/Install\ macOS\ `MacOS`.app/Contents/Resources/createinstallmedia \
    --volume /Volumes/`UNTITLED` \
    --nointeraction && say Boot Drive Created

Erasing disk: 0%... 10%... 20%... 30%... 100%
Copying to disk: 0%... 10%... 20%... 30%... 40%... 50%... 60%... 70%... 80%... 90%... 100%
Making disk bootable…
Install media now available at “/Volumes/Install macOS `MacOS`”
```
