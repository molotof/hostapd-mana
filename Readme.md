hostapd MANA w/RTL8188 chipsets!
================
This project is a fork off of the Mana-Toolkit's modified hostapd (sensepost/hostapd-mana).
Functionality of their HostAPD has not been changed, I have just bundled a couple different projects together.

Added Realtek's RTL8188 driver to HostAPD from http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true

Patched Realtek's drivers with pritambaral/hostapd-rtl871xdrv's patches and modified drivers

Patched with OpenWRT's No-scan patch https://dev.openwrt.org/browser/trunk/package/network/services/hostapd/patches/300-noscan.patch

The goal of this was to add better pen-testing support for the Raspberry Pi/Pi 2. Many Raspberry Pi users rely on the RTL8188 chipsets
due to their small size and low power usage. Unfortunately, this chipset isn't supported in AP mode in HostAPD, natively. Thus, making
it more difficult to take advantage of the Pi's small size and concealability. This project aims to close that gap.

I will do my best to update this as HostAPD-Mana/HostAPD are updated.

hostapd MANA
================
by Dominic White (singe) & Ian de Villiers @ sensepost (research@sensepost.com)

Overview
--------
A access point (evilAP) first presented at Defcon 22.

More specifically, it contains the improvements to KARMA attacks we implemented into hostapd, as well as the ability to rogue EAP access points.

This will track the hostapd releases, although at a somewhat lagged pace depending on time. At the time of publication this was up to date with the latest hostapd-2.3 branch.

Contents
--------

It contains:
* hostapd-mana - modified hostapd that implements our new karma attacks
* crackapd - a tool for offloading the cracking of EAP creds to an external tool and re-adding them to the hostapd EAP config (auto crack 'n add)

Installation
------------

The build instructions are exactly the same as hostapd's, and can be found in hostapd/README

Pre-Requisites
--------------

_Hardware_

You'll need a wifi card that supports master mode. You can check whether it does by running:
    iw list
You want to see "AP" in the output. Something like:
```
Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * mesh point
```
More information at https://help.ubuntu.com/community/WifiDocs/MasterMode#Test_an_adapter_for_.22master_mode.22

Three cards that have been confirmed to work well, in order of preference are:
* Ubiquiti SR-71 (not made anymore :(, chipset AR9170, driver carl9170 http://wireless.kernel.org/en/users/Drivers/carl9170 ) 
* Alfa Black AWUS036NHA (chipset Atheros AR9271, buy at http://store.rokland.com/products/alfa-awus036nha-802-11n-wireless-n-usb-wi-fi-adapter-2-watt ) 
* TP-Link TL-WN722N (chipset Atheros AR9271 )

Note, the silver Alfa does not support master mode and will not work.

Running
-------

You'll need to generate a valid configuration file. Some example of these are included in the MANA toolkit at https://github.com/sensepost/mana

License
-------

The patches included in hostapd-mana by SensePost are licensed under a Creative Commons Attribution-ShareAlike 4.0 International License (http://creativecommons.org/licenses/by-sa/4.0/) Permissions beyond the scope of this license may be available at http://sensepost.com/contact us/. hostapd's code retains it's original license available in COPYING.
