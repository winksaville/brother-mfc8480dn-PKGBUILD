# brother-mfc8480dn-PKGBUILD
This is a slight modification for the (dcp7065dn)[https://aur.archlinux.org/packages/brother-dcp7065dn/].
Basically just changing the dcp7065 text to mfc8480.

General Printing dependencies I installed:
- sudo pacman -S system-config-printer
- sudo pacman -S cups
- sudo pacman -S libcups
- sudo pacman -S ghostscript gsfonts
- sudo pacman -S cups-pdf
- sudo pacman -S namcap


To install this driver:
- clone this repo
- makepkg
- sudo pacman -U brother-mfc8480dn-3.1.0-1-x86_64.pkg.tar.x

After installing using pacman -U I could add the printer using (localhost:631)[http://localhost:631]. After
doing that the printer would show up but nothing could be printed.

Eventually I stumbled on "Avahi Zeroconf Browser" and it shows 3 instances of the printer and I saw what
IP address the printer was. I then used "Printer Settings" changed the "Device Uri" field to
"socket://192.168.0.135:9100" by using "Device Uri" "Change..." button. In that dialog I looked under
"Network Printer" and selected "AppSocket/HP JetDirect" and setting
"Host" to "192.168.0.135" and leaving the "Port number" at its default which was "9100".

I could then print to the printer! Although no gaurantees these steps will work a second time as
there were many other things I tried before stumbling across this technique.
