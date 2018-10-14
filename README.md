# Contents #
* [Fake Hotspot](#fake-hotspot)


## Fake Hotspot
First we need to install configure a few things
* dnsmasq

dnsmasq.conf
```
interface=wlan0
dhcp-range=10.0.0.1,10.0.0.100,255.255.255.0,12h
dhcp-option=3,10.0.0.1
dhcp-option=6,10.0.0.1
address=/#/127.0.0.1
address=/bing.com/10.0.0.1
```

* hostapd

hostapd.conf
```
interface=wlan0
driver=nl80211
ieee80211ac=1
ieee80211d=1
ssid=infosec
channel=1
wpa=2
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
wpa_passphrase=infosec1
```

* iptables

For iptables, we have many options depend on the usage.
To enable internet connection on your hotspot type :
```
iptables -A FORWARD -i wlan0 -j ACCEPT -o eth0 #receive
iptables -A POSTROUTING -t nat -o eth0 -j MASQUERADE #send

```



### Powershell
