# axolotl-mobian-package
Here you can find an arm64 package of [Axolotl](https://github.com/nanu-c/axolotl) for Mobian or other Debian-based distros in version 1.0.9.

This version of Axolotl was cross-compiled from scratch using the repository Makefile and has the following main improvements:

  * Fix 'Verifiy Identity'
  * Fix option to mute groups
  * Fix links opening inside of axolotl on ubuntu touch
  * Fix rendering of expire timer in chats with self destroying messages
  * Remove "Upstream Changes" Warning Message
  * Add support for voice notes
  * Add support for joining groups
  * Fix opening document attachments
  * Fix Messages with special characters (e.g. "<") not displayed correctly
  * Update many dependencies
  * Fix receiving messages by waking up crayfish childprocess from sleep

Group invitation links are not yet working.

Wayland support via the Electron Ozone platform is still deactivated due to the letter input bug (still ü, C and V are missing, too) - more information [here](https://github.com/nanu-c/axolotl/issues/635).


# Use
Download the Debian package file with
```
wget https://github.com/nuehm-arno/axolotl-mobian-package/raw/v1.0.9-1/axolotl_1.0.9-1_arm64.deb
```
and start the installation with
```
sudo apt install ./axolotl_1.0.9-1_arm64.deb
```

# App Menu Entry
This installation method provides you with one App Menu Entry "Axolotl". It can be altered with
```
sudo nano /usr/share/applications/axolotl.desktop
```

# First Start
The first start of Axolotl takes some time, because local folders have to be created and because the Electron source package has to be downloaded (~100Mb).

# Daemonized Server Setup
Using this setup, Axolotl can be run as a daemon in the background and a browser (cog or Firefox-ESR) as user interface.
There are three more desktop files for this setup in this repo and you can copy these into your applications folder via
```
git clone --depth=1 https://github.com/nuehm-arno/axolotl-mobian-package
```
```
sudo cp $HOME/axolotl-mobian-package/axolotl-server.desktop /usr/share/applications/
```
```
sudo cp $HOME/axolotl-mobian-package/axolotl-browser-cog.desktop /usr/share/applications/
```
```
sudo cp $HOME/axolotl-mobian-package/axolotl-browser-firefox.desktop /usr/share/applications/
```
Furthermore, you need cog installed on your system
```
sudo apt install cog=0.8.1-1
```

If you want Axolotl as daemon started automatically at login, copy the desktop file into the Gnome autostart folder with
```
sudo cp $HOME/axolotl-mobian-package/axolotl-server.desktop /etc/xdg/autostart
```

# Updates
If a new version of Axolotl or this package is out, you can simply use the installation command to update the app. Your local files will be kept, but a backup is recommended.


# Removing Axolotl
Axolotl shall be removed via
```
sudo apt remove --purge axolotl
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
