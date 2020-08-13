# PiShrink dockerized

**PiShrink** automatically shrink a Raspberry Pi image in order to reduce the final image size.

It's great for saving disk space or sharing your Pi image on the Internet.

This project is a dockerized version of the [PiShrink bash script](https://github.com/Drewsif/PiShrink) by Drew Bonasera.

![Release][release-install-shield] [![License][license-shield]](LICENSE.md) [![Twitter][twitter-shield]](https://twitter.com/mgomesborges)

## Usage

1. Make a copy of a Raspberry Pi SD card that you want to shrink ([see instructions here](https://github.com/mgomesborges/raspberry-pi/blob/master/setup/clone-sd-card.md)).

2. Using the Terminal, access the directory containing the Raspberry Pi image:

    ```bash
    cd ~/Directory-with-RPi-image
    ```

3. Run PiShrink dockerized:

    ```bash
    docker run --privileged=true --rm \
        --volume $(pwd):/workdir \
        mgomesborges/pishrink \
        pishrink -pZv IMAGE.img NEW-IMAGE.img
    ```

## PiShrink options

```
pishrink [-adhrspvzZ] IMAGE.img NEW-IMAGE.img

-s      Do not expand filesystem when image is booted the first time
-v      Enables more verbose output
-r      Use advanced filesystem repair option if the normal one fails
-z      Compress image after shrinking with gzip
-Z      Compress image after shrinking with xz
-a      Compress image in parallel using multiple cores
-p      Remove logs, apt archives, dhcp leases and ssh hostkeys
-d      Write debug messages in a debug log file
```

If you specify the `NEW-IMAGE.img` parameter, the script will make a copy of `IMAGE.img` and work off that. You will need enough space to make a full copy of the image to use that option.

Check out [PiShrink GitHub](https://github.com/Drewsif/PiShrink/blob/master/README.md) for more details.

## Author

* [Marcos Gomes-Borges](https://github.com/mgomesborges)

## License

The source code is licensed under the [MIT license](LICENSE.md).

The content of this project itself is licensed under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0).

[twitter-shield]: https://img.shields.io/twitter/follow/mgomesborges?label=Follow&style=social
[release-install-shield]: https://img.shields.io/badge/Release-13--Aug--2020-blue
[license-shield]: https://img.shields.io/github/license/mgomesborges/mac-dev-setup.svg