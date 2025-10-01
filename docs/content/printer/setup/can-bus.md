# Can Bus Setup

There are some changes we need to make on the rpi in order
to ensure the CAN bus is up for use by klipper or for firmware updates

  * https://www.pragmaticlinux.com/2021/07/automatically-bring-up-a-socketcan-interface-on-boot

## Diagnosing Problems

### List State

This command will list the current state of the CAN bus.
Including it's speed and if it's up or down.
```bash
ip -det addr
ip link show can0
ifconfig can0
```

### Manually Bring Bus Up / Down

To manually bring the bus up or down
```bash
sudo ip link set down can0
sudo ip link set up can0
```

### List Katapult devices

To list all Katapult devices found over the CAN bus
```bash
python3 ~/katapult/scripts/flashtool.py -i can0 -q
```

### systemd-networkd

The can bus should be configured as part of
`/etc/systemd/network/25-can.network`

But based on this
```
sudo systemctl status systemd-networkd
sudo systemctl restart systemd-networkd
```

Shows that it configures the speed but doesn't bring it up
Could this be a kernel bug assoiated with USB adapters?

https://lkml.rescloud.iu.edu/2507.2/00068.html
