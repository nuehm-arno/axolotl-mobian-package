# axolotl-mobian-package
Here you can find an arm64 package of Axolotl (https://github.com/nanu-c/axolotl) for Mobian in version 0.9.8.

# Use
Download the Debian package file with
```
git clone https://github.com/nuehm-arno/axolotl-mobian-package
```
and start the installation with
```
cd axolotl-mobian-package
sudo apt install ./axolotl_0.9.8-2_arm64.deb
```

# Important
If you have used the Axolotl Installer for Mobian (https://github.com/nuehm-arno/axolotl-mobian-installer) on your current system, you should follow these steps to remove at least the old desktop file(s) before installing the Debian package file.
```
sudo rm /usr/share/applications/axolotl.desktop
```
(or similar, if you created other starters for Axolotl)

To remove the old build/installation of Axolotl completely from your system, follow these steps
```
#if you have no other go projects
sudo rm go
#if you don't need these packages somewhere else
sudo apt remove --purge npm nodejs mercurial golang python
```

# App Menu Entry
This installation method provides you with one App Menu Entry "Axolotl". It can be altered with
```
sudo nano /usr/share/applications/axolotl.desktop
```

# First Start
The first start of Axolotl takes some time, because local folders have to be created.

# Daemonized Server Setup
Using this setup, Axolotl can be run as a daemon in the background and a browser (Firefox-ESR) for user interface.
There are two more desktop files for this setup
```
/usr/share/applications/axolotl-server.desktop
/usr/share/applications/axolotl-browser.desktop
```
These files have the "NoDisplay=true" flag and are not shown in the App Menu. This can be achieved by changing the value to "false".

If you want Axolotl as daemon started automatically at login, copy the desktop file into the Gnome autostart folder with
```
sudo cp /usr/share/applications/axolotl-server.desktop /etc/xdg/autostart
```

# Updates
If a new version of Axolotl or this package is out, you can simply use the installation command to update the app. Your local files will be kept, but a backup is recommended.

# Removing Axolotl
Axolotl shall be removed via
```
sudo apt remove --purge axolotl
```
While removing the app, you will be asked, whether you want to keep your local files (configuration, registration, contacts and messages) or if you want them to be deleted.
Please choose careful.

# Axolotl Qt
There is an option to use Axolotl with Qt via qmlscene, but this isn't working at the moment.

If you are willing to give it a try, edit the desktop file and change the "#" between the two "Exec=" lines. You will also need the following dependencies
```
sudo apt update && sudo apt install qmlscene qml-module-qtwebsockets qml-module-qtmultimedia qml-module-qtwebengine
sudo apt-get install qml-module-qtquick.controls
sudo apt-get install qml-module-qtquick.dialogs
```

# Personal Data
Your configuration, registration, contact and message files are stored here
```
~/.config/textsecure.nanuc
~/.local/share/textsecure.nanuc
```
and you should backup these folders regularly and espescially before removing or re-installing Axolotl.
