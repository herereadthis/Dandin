# Dandin

```bash
npm install
npm run live
```

The directory `portal` contains a highly modified version of the Ubiquiti Legacy JSP Guest Portal that comes with the USG

The directory `portal-archive` contains the original Legacy JSP Guest Portal files.

Go into your controller, which should be http://`<IP_ADDRESS>`:8443

* In Wireless Network:
  * edit wireless network and check "Apply guest policies"
* In Guest Control,
  * Guest Policies:
    * Check "Enable Guest Portal"
    * Choose "Simple Password" and "Expiration"
  * Portal Customization:
    * Choose "Legacy JSP"
    * Check "Override templates with custom changes"

Raspberry Pi Controller

* Some prerequisites:
  ```bash
  # install zip
  sudo apt-get install zip
  ```
* The Unifi directory, or `<unifi_base>` is `/usr/lib/unifi`
* all the junk is located in /usr/lib/unifi/data/sites/default/portal
* You will have to change permissions on the directories to get to them
  ```bash
  cd /usr/lib/unifi
  # see permissions
  la -la
  sudo chmod 777 data
  cd data
  # and so on, until you reach the default directory
  zip -r site.zip portal
  mv site.zip ~/
  ```
* copy the contents to your local machine to do work.
  ```bash
  scp pi@lime:/home/pi/foo.zip foo.zip
  ```

## How to install Unifi Controller on Raspberry Pi

Go to the Unifi site and download the Unifi Controller for Debian/Linux

```bash
# install the Unifi Controller
sudo dpkg -i unifi_sysvinit_all.deb
# After installation, you will get a warning about missing packages. Install them.
sudo apt-get install -f
# Check the status; it should say running
sudo service unifi status
# It may not be running because Raspbian's version of Java is incompatible
sudo apt-get install openjdk-8-jre-headless -y
# If you ever need to upgrade the controller
sudo apt-get upgrade unifi
```

## Sources

* [(ARCHIVED) UniFi - Legacy Hotspot Portal Customization](https://help.ubnt.com/hc/en-us/articles/205143830--ARCHIVED-UniFi-Legacy-Hotspot-Portal-Customization)
