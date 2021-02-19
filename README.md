# PomodoneApp-Problem-Resolved

PomodoneApp does not launch on Ubuntu 20.04\
Error Message:\
(pomodoneapp:35323): Pango-ERROR **: 13:06:27.995: Harfbuzz version too old (1.4.2)\
Trace/breakpoint trap (core dumped)

#### Fix the problem:
```bash
$ cd /tmp
$ wget http://launchpadlibrarian.net/438303557/libpango-1.0-0_1.42.4-7_amd64.deb
$ wget http://launchpadlibrarian.net/438303558/libpangocairo-1.0-0_1.42.4-7_amd64.deb
$ wget http://launchpadlibrarian.net/438303559/libpangoft2-1.0-0_1.42.4-7_amd64.deb
$ cd /opt/PomoDoneApp
$ sudo dpkg -x /tmp/libpango-1.0-0_1.42.4-7_amd64.deb .
$ sudo dpkg -x /tmp/libpangocairo-1.0-0_1.42.4-7_amd64.deb .
$ sudo dpkg -x /tmp/libpangoft2-1.0-0_1.42.4-7_amd64.deb .
```

##### To run the app:
```bash
$ LD_LIBRARY_PATH=/opt/PomoDoneApp/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH ./pomodoneapp
```

if you want to run it in the command line, add the last line to the ```~/.bashrc``` file and set an Alias to that:
```bash
alias pmdapp='LD_LIBRARY_PATH=/opt/PomoDoneApp/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH opt/PomoDoneApp/pomodoneapp'
```

you can also run the app from your desktop:
To create a simple custom ```.desktop``` you will need to add these entries to a ```.desktop``` file in ```~/.local/share/applications/```
```bash
$ nano ~/.local/share/applications/pomodoneapp.desktop
```
Paste these lines to that:
```
Name=PomodoneApp
Comment=
Exec= LD_LIBRARY_PATH=/opt/PomoDoneApp/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH /opt/PomoDoneApp/pomodoneapp
Icon=
Terminal=false
Type=Application
StartupNotify=truen
```

```bash
$ cp ~/.local/share/applications/pomodoneapp.desktop ~/Desktop
$ chmod +x ~/Desktop/pomodoneapp.desktop
```
