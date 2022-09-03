# vzlogger package for openwrt
This is an openwrt package for the vzlogger https://github.com/volkszaehler/vzlogger from https://www.volkszaehler.org/

This is not really well tested as I figured out that the IrDA on my SmartMeter is not even activated. But it compiles and 
vzlogger runs fine.

It contains some simple vzlogger.conf which (of course) needs to be adapted for your usecase.

## Howto build
### Install package feed
```
./scripts/feeds update
./scripts/feeds install -a
```

### Add this repo to the packages (I always just add it to the package subfolder within the openwrt source tree)
```
make menuconfig # Select vzlogger
make -j4 V=s
```

When vzlogger was enabled as (*) it is directly integrated into the sysupgrade image, otherwise you need to manually install
the .ipk package

## PRs
Feel free to send PRs ;)
