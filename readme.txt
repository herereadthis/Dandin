# Dandin

The directory `portal` contains a highly modified version of the Ubiquiti Legacy JSP Guest Portal that comes with the USG

The directory `portal-archive` contains the original Legacy JSP Guest Portal files.

In Wireless Network, edit wireless network and check "Apply guest policies"
In Guest Control > Guest Policies, check "Enable Guest Portal"
Also, for now, choose "Simple Password" and "Expiration"
In Guest Control > Portal Customization, choose "Legacy JSP"
Then Check "Override templates with custom changes"
In RPi controller directory, Unifi directory is /usr/lib/unifi
all the junk is located in /usr/lib/unifi/data/sites/default
You will have to change permissions on the directories to get to them,
sudo chmod +rwx data
hard to do this over ssh, so let's zip up the default directory
sudo apt-get install zip
ls -la to see permission octal
return with chmod 750 data
zip -r foo.zip portal
mv foo.zip ~/
then, on local machine
scp pi@lime:/home/pi/foo.zip foo.zip
