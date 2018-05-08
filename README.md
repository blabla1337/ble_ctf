## BLE Capture the Flag
The purpose of BLE CTF is to teach the core concepts of Bluetooth Low Energy client and server interactions.  While it has also been built to be fun, it was built with the intent to teach and reinforce core concepts that are needed to plunge into the world of Bluetooth hacking.  After completing this CTF, you should have everything you need to start fiddling with any BLE GATT device you can find.

## Setting Up the CTF
In order to set up the CTF you will need the following:
1. The code in this repository to build the CTF GATT server
2. An esp32 microcontroller
3. A computer (preferably OSX or Linux) with a bluetooth controller or a bluetooth usb dongle
4. Bluetooth tools such as Bluez tools (hcitool, gatttool, etc) or [bleah](https://github.com/evilsocket/bleah)

To get setup, [read this documentation](docs/setup.md)

## Flags

### How to Submit Flags

Before you can submit flags, you have to discover the Bluetooth MAC address of your device.  Here are a couple example commands to help you find your device:

Discover MAC using hcitool:   
```` sudo hcitool blescan ````

Discover MAC using bleah:   
```` sudo bleah ````

Now that you have found your device’s MAC address, you can now communicate with it.  Before we get started with flags, let’s check out how we can see our current score.  In order to see where you are in the CTF, you can read from handle 12 on the device to see how many flags you have.  The following are example commands of how to view your current score.  Make sure you replace the MAC address in the example commands with the MAC address of your device. 

Show score with gatttool:  
```` gatttool -b 30:ae:a4:20:79:da --char-read -a 12  ````

Show score with bleah:  
```` sudo bleah -b "30:ae:a4:20:79:da" -h 12 ````

Ok, ok, ok, on to the flags! All flags are md5 sums truncated to 20 characters to avoid MTU limits by some hardware.  They can be submitted to the gatt server on handle 42.  The following are examples of how to submit a flag.  Make sure you replace the MAC address in the example commands with the MAC address of your device:   

Submit using gatttool:  
```` gatttool -b 30:ae:a4:20:79:da --char-write-req -a 0x002f -n 0x0001 ````

Submit using bleah:  
```` sudo bleah -b "30:ae:a4:20:79:da" -u "0000ff03-0000-1000-8000-00805f9b34fb" -d "hello world" ````

### Flag Hints
| Flag | Description | Hint |
| ------- | ----------------------------- | ------- |
| Flag 1 | This flag is a gift and can only be obtained from reading the hint! | [Read Me!](docs/hints/flag1.md) |
| Flag 2 | Learn about discoverable device attributes | [More](docs/hints/flag2.md) |
| Flag 3 | Learn how to read handles | [More](docs/hints/flag3.md) |
| Flag 4 | Read handle puzzle fun | [More](docs/hints/flag4.md) |
| Flag 5 | Learn about BT client device attributes | [More](docs/hints/flag5.md) |
| Flag 6 | Learn about connection attributes | [More](docs/hints/flag6.md) |
| Flag 7 | Learn about reading and writing to handles | [More](docs/hints/flag7.md) |
| Flag 8 | Learn about brute write fuzzing | [More](docs/hints/flag8.md) |
| Flag 9 | Learn about notifications | [More](docs/hints/flag9.md) |
| Flag 10 | Learn about BT broadcast messages | [More](docs/hints/flag10.md) |
| Flag 11 | Learn about responses | [More](docs/hints/flag11.md) |
| Flag 12 | Learn about connection security attributes | [More](docs/hints/flag12.md) |
| Flag 13 | Learn about indications | [More](docs/hints/flag13.md) |
| Flag 14 | Handle puzzle fun | [More](docs/hints/flag14.md) |
| Flag 15 | Hard handle puzzle fun | [More](docs/hints/flag15.md) |
| Flag 16 | Harder handle puzzle fun | [More](docs/hints/flag16.md) |
| Flag 17 | Harderer handle puzzle fun | [More](docs/hints/flag17.md) |
| Flag 18 | Abuse me | [More](docs/hints/flag18.md) |
| Flag 19 | Exhaust me | [More](docs/hints/flag19.md) |
| Flag 20 | Not gonna tell! | [More](docs/hints/flag20.md) |
