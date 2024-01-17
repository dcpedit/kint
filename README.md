# KinT Blackpill Edition

![kinesis-3](https://user-images.githubusercontent.com/800930/186173690-8d34ccd0-7eec-4b3d-93a0-488730113e12.jpg)

This is a fork of Michael Stapelberg's [KinT project](https://github.com/kinx-project/kint) with the following modifications:

* Replaced Teensy with STM32F411 Blackpill controller (`blackpill` directory)
* Reduced PCB size to 100 x 86 mm
* Use Vial firmware.  Source code is in my [fork of Vial](https://github.com/dcpedit/vial-qmk-dev/tree/vial/keyboards/dcpedit/kint_bp)

## Files for JLCPCB
Located in the directory `/blackpill/production`

## Parts for Build
| Component              | Qty | Notes |
| ---------              | --- | ----- |
| SMD LEDs               | 4   | Can be any color [Link](https://octopart.com/apt3216qbc%2Fd-kingbright-5355642?r=sp)
| SMD 10k resistors      | 4   | [Link](https://octopart.com/crcw120610k0fkeac-vishay-20811529)
| Molex 13 pin connectors| 4-6 | Needed if you don't want to desolder old ones [Link](https://octopart.com/39-53-2135-molex-7670149?r=sp)
| STM32F411 Blackpill    | 1   | AliExpress [Link](https://www.aliexpress.us/item/3256801269871873.html)
| Panel mount USB-C      | 1   | Amazon [Link](https://a.co/d/cRoqHqx)
| Socketed headers       |     | Only needed if you want to socket your Blackpill.

## Bluetooth + ZMK build
You can now use the Pillbug dev board along with ZMK firware to make this a wireless mod.  Basically, just swap out the Blackpill with a Pillbug and add a battery.

| Component              | Qty | Notes |
| ---------              | --- | ----- |
| Pillbug                | 1   | MechWild [Link](https://mechwild.com/product/pillbug/)
| 2000 mAh battery       | 1   | Amazon [Link](https://a.co/d/hlTVT1p)

v2022-08-05 of the PCB requires you to bridge the 3.3v pins with a wire.  The diagram below shows you which pins.

<img width="300" alt="wire bridge" src="https://github.com/dcpedit/kint/assets/800930/58853577-421a-4007-8ab4-ac768d001421">

The current version in the repo does not require this.

If you're using a battery that's larger than 500 mAh, short JP1 on the back of the Pillbug to enable "Charge Boost" (changes charge rate from 100mA to 500mA)

## Firmware
Vial:
* `/firmware/dcpedit_kint_bp_vial.bin` - Default keymap (stock Kinesis)
* `/firmware/dcpedit_kint_bp_vial_6layers.bin` - Support for 6 layers

ZMK:
* `/firmware/zmk_default.uf2` - Default keymap (stock Kinesis)
* `/firmware/zmk_reset.uf2` - Resets PillBug board for BT connectivity issue on MacOS