# haiku-fan-control

This project contains some simple code for controlling SenseME-enabled Haiku 
fans from BigAss Solutions.

This implementation is based off the protocol decoding by Bruce Pennypacker.
You can see his blog posts at http://bruce.pennypacker.org/tag/haiku/.

# haikuctl

## Help

```
usage: haikuctl [-h] --address IP --name DEVICE_NAME [--device DEVICE_TYPE]
                [--state {on,off,partial}] [--level DEVICE_LEVEL]

optional arguments:
  -h, --help            show this help message and exit
  --address IP, -H IP   Address of the SenseME node
  --name DEVICE_NAME, -n DEVICE_NAME
                        Name of the fan, wall control, or light location to
                        control
  --device DEVICE_TYPE, -d DEVICE_TYPE
                        Type of device to send the command to (default: fan)
  --state {on,off,partial}, -s {on,off,partial}
                        Set device state (default: on)
  --level DEVICE_LEVEL, -l DEVICE_LEVEL
                        Set device speed/level
```

### Note

Device level is set in increments from 0 to 15, with 0 corresponding to
lowest/off and 15 corresponding to fastest/brightest.

Device name is the room location you placed the device in with the Haiku
iPhone/Android app. This name is auto-uppercased within the script.

IP address is the address of the device.

This script currently does *not* control 

* Woosh mode, 
* enabling/disabling Auto-on,
* Smart settings
* Scheduling


## Turn off a light in the Office

```
haikuctl -H 192.168.181.199 -n Office -d light -s off
```
## Turn on a light in the Office

```
haikuctl -H 192.168.181.199 -n Office -d light -s on
```

## Set the level on a light in the Office

```
haikuctl -H 192.168.181.199 -n Office -d light -s partial -l 8
```

## Turn off a fan in the Office

```
haikuctl -H 192.168.181.199 -n Office -d fan -s off
```
## Turn on a fan in the Office

```
haikuctl -H 192.168.181.199 -n Office -d fan -s on
```

## Set the speed on a fan in the Office

```
haikuctl -H 192.168.181.199 -n Office -d fan -s partial -l 8
```
