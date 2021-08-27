# axolotl-mobian-package
Here you can find an arm64 package of [Axolotl](https://github.com/nanu-c/axolotl) for Mobian or other Debian-based distros in version 1.0.2.

This version of Axolotl was built from scratch using the repository Makefile and has the following main improvements:

- Fix Linking Signal Desktop
- Fix setting a password
- Code quality improvements

Still, the current way to join v2groups is by being added by another user in the group. Group invitation links are not yet working. [Here](https://github.com/nanu-c/axolotl/pull/460) is a list of things to complete for basic v2group support in Axolotl.

# Use
Download the Debian package file with
```
git clone --depth=1 https://github.com/nuehm-arno/axolotl-mobian-package
```
and start the installation with
```
cd axolotl-mobian-package && sudo apt install ./axolotl_1.0.2-1_arm64.deb
```

# App Menu Entry
This installation method provides you with one App Menu Entry "Axolotl". It can be altered with
```
sudo nano /usr/share/applications/axolotl.desktop
```

# First Start
The first start of Axolotl takes some time, because local folders have to be created and because the Electron source package has to be downloaded (~80Mb).

# Daemonized Server Setup
Using this setup, Axolotl can be run as a daemon in the background and a browser (cog or Firefox-ESR) as user interface.
There are three more desktop files for this setup in this repo and you can copy these into your applications folder via
```
cd axolotl-mobian-package && sudo cp axolotl-server.desktop /usr/share/applications/
cd axolotl-mobian-package && sudo cp axolotl-browser-cog.desktop /usr/share/applications/
cd axolotl-mobian-package && sudo cp axolotl-browser-firefox.desktop /usr/share/applications/
```
Furthermore, you need cog installed on your system
```
sudo apt install cog
```

If you want Axolotl as daemon started automatically at login, copy the desktop file into the Gnome autostart folder with
```
cd axolotl-mobian-package && sudo cp axolotl-server.desktop /etc/xdg/autostart
```

# Updates
If a new version of Axolotl or this package is out, you can simply use the installation command to update the app. Your local files will be kept, but a backup is recommended.


# Removing Axolotl
Axolotl shall be removed via
```
sudo apt remove --purge axolotl
```

If you have used the [Axolotl Installer for Mobian](https://github.com/nuehm-arno/axolotl-mobian-installer) on your current system, you should follow these steps to remove at least the old desktop file(s) before installing the Debian package file.
```
sudo rm /usr/share/applications/axolotl.desktop
```
(or similar, if you created other starters for Axolotl)

To remove the old build/installation of Axolotl completely from your system, follow these steps
```
#if you have no other go projects
sudo rm -rf go
#if you don't need these packages somewhere else
sudo apt remove --purge npm nodejs mercurial golang python
```

# Axolotl Qt
IMPORTANT: Axolotl Qt is not further developed and will be deprecated in the future.

There is an option to use Axolotl with Qt via qmlscene, but this isn't working reliably at the moment.

If you are willing to give it a try, edit the desktop file and change the "#" between the two "Exec=" lines. You will also need the following dependencies
```
sudo apt update && sudo apt install qmlscene qml-module-qtwebsockets qml-module-qtmultimedia qml-module-qtwebengine
sudo apt-get install qml-module-qtquick.controls
sudo apt-get install qml-module-qtquick.dialogs
```

# Personal Data
Your configuration, registration, contact and message files are stored here
```
~/.config/textsecure.nanuc/
~/.local/share/textsecure.nanuc/
```
and you should backup these folders regularly and espescially before removing or re-installing Axolotl.


# Disclaimer
This package is unofficial and not uploaded into the Debian repos.


# Reporting Issues
Please report issues regarding Axolotl using the official [Axolotl issue tracker](https://github.com/nanu-c/axolotl/issues).
