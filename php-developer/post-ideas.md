# Post ideas

* Getting Python up and running - link to this post: http://markfrimston.co.uk/articles/30/quick-python-web-setup-for-apache
* Hello World in Node.js
* How to change package build options in Ubuntu
* Member initialisation lists in C++
* Multi-dimensional arrays in C++
* WordPress 4.1
* Mojolicious posts on Josetteorama
* How to install virtual box guest additions in an Ubuntu VM (dkms + ISO)
* Pibrella
* How to send emails using telnet
* How to test web servers using telnet

## RPi eduroam

In /etc/wpa_supplicant/wpa_supplicant.conf

network = {
  identity="mbax9ab9"
  password="password"
  eap=PEAP
  anonymous_identity="@manchester.ac.uk"
  phase1="peaplabel=0"
  phase2="auth=MSCHAPV2"
  priority=999
  disabled=0
  ssid="eduroam"
  scan_ssid=0
  mode=0
  auth_alg=OPEN
  proto=RSN
  pairwise=CCMP
  key_mgmt=WPA-EAP
  proactive_key_caching=1
}


In /etc/network/interfaces:

allow-hotplug wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B

## Installing XFCE on RPi

Install XFCE: `apt-get install xfce4`

Install slim: `apt-get install slim`

Choose Slim from the list of options when running the above command.

Reboot, use F1 to switch between desktops (startxfce4 is the one you want).

## Writing Perl modules using Dist::Zilla

## PHPExcel examples

Demonstrate various simple tasks, such as formatting, iterators etc.

## Functions and local variables in Bash

## SSH config

```
Host example 
  HostName example.org 
  User paul
  Port 2200                            
```
                                                                             
`ssh example` becomes `ssh -p 2200 paul@example.org`
