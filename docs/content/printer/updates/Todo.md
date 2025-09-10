# TODO

Mainboard is updated
but I still need to update the CAN board
running klipper service with this as is seems to lock the machine

For now klipper is disabled via
```
sudo systemctl disable klipper
```

When the head board is updated we can re-enable with
```
sudo systemctl enable klipper
```
