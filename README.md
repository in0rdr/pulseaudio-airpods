<!-- ![Mastodon Follow](https://img.shields.io/mastodon/follow/28693?domain=https%3A%2F%2Fmastodon.online&style=flat-square) -->
<!-- ![Keybase PGP](https://img.shields.io/keybase/pgp/akhiljalagam?style=flat-square)
![Keybase BTC](https://img.shields.io/keybase/btc/akhiljalagam?style=flat-square)
 -->
# pulseaudio-airpods 💃🕺
a shell script for managing airpods and airpods pro on linux.  

## Dependencies
* https://build.opensuse.org/package/show/home:tdoerges/phonesim
* https://software.opensuse.org/package/ofono
* https://software.opensuse.org/package/ofono-tests
* OpenSuse Leap 15.1

```
sudo zypper addrepo https://download.opensuse.org/repositories/home:tdoerges/openSUSE_Leap_15.1/home:tdoerges.repo
sudo zypper refresh
sudo zypper install phonesim ofono ofono-tests
git clone https://github.com/in0rdr/pulseaudio-airpods.git /opt/ofono
```

Configure phonesim modem:
```
tee /etc/ofono/phonesim.conf <<EOF
# This is a sample file for the phonesim configuration
#
# It should be installed in your oFono system directory,
# e.g. /etc/ofono/phonesim.conf
#
# Each group is parsed as a modem device
#
# Each group shall at least define the address and port
#   Address = <valid IPv4 address format>
#   Port = <valid TCP port>

[phonesim]
Address=127.0.0.1
Port=12345
EOF
```

## Tweak the script for first time
replace MAC and card name in the script
```
AIRPODS_MAC='4C:6B:E8:80:46:84' # it should be somewhere in blueman-manager  
AIRPODS_NAME='bluez_card.4C_6B_E8_80_46_84' # you can find this using 'pactl list cards' command  
```

## Usage
```
pusleaudio-airpods connect/toggle_profile/disconnect
```

## Check

Check the modem:
```
/usr/lib64/ofono/test/list-modems 
[ /phonesim ]
    Online = 0
    Powered = 1
    Lockdown = 0
    Emergency = 0
    Manufacturer = MeeGo
    Model = Synthetic Device
    Revision = REV1
    Serial = 1234567890
    Interfaces = org.ofono.VoiceCallManager org.ofono.SimManager 
    Features = sim 
    Type = hardware
    [ org.ofono.VoiceCallManager ]
        EmergencyNumbers = 118 110 08 911 000 112 999 119 
    [ org.ofono.SimManager ]
        Present = 1
        CardIdentifier = 8949222074451242066
        FixedDialing = 0
        BarredDialing = 0
        SubscriberNumbers = 
        LockedPins = 
        PreferredLanguages = de en it fr es nl 
        PinRequired = none
        Retries = 
```

## Note
you should first pair your airpods using blueman and trust them to use this script

## Links

https://zambrovski.medium.com/using-bluetooth-headset-on-ubuntu-790ce6eecc2

## Contributions are welcome

## Say thanks:
  
  Just letting me know you're enjoying this plugin is a great way to say thanks!
  
  You can do so by staring the GitHub repo.
  
## Troubles?
  
  If you have any kind of trouble with it, just let me now by raising an issue on
  the GitHub issue tracker here:

  It should be there 👆 👀
