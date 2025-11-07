---
layout: home
title: Run Debian on Sophgo cv181x/sg200x based boards
---

## How to Install?

### Individually

You will also need to use an image matching your board, which are available from:

* [Pairman/sophgo-sg200x-debian/releases](
https://github.com/Pairman/sophgo-sg200x-debian/releases/latest)

### About the images

Details about the content and some hints howto configure itc an be found in the readme here:

* [Pairman/sophgo-sg200x-debian](
https://github.com/Pairman/sophgo-sg200x-debian)

### Add a Debian Repository

This step is only required if you are using an older image or build your own.  
If you have image version v1.5.20 or later this is already included.

Download the [public key](pairman-packages.asc) and put it in
`/etc/apt/keyrings/pairman-packages.asc`. You can achieve this with:

```
wget -qO- {{ site.url }}/pairman-packages.asc | sudo tee /etc/apt/keyrings/pairman-packages.asc >/dev/null
```

Next, create the source in `/etc/apt/sources.list.d/`

```
echo "deb [arch=riscv64 signed-by=/etc/apt/keyrings/pairman-packages.asc] {{ site.url }}/deb stable sg200x" | sudo tee /etc/apt/sources.list.d/pairman-packages.list >/dev/null
```

To get all packages you can add the repository matching the board-specific image. For example, ```licheervnano-e```:

```
echo "deb [arch=riscv64 signed-by=/etc/apt/keyrings/pairman-packages.asc] {{ site.url }}/deb stable sg200x licheervnano-e" | sudo tee /etc/apt/sources.list.d/pairman-packages.list >/dev/null
```

Then run `apt update && apt install -y` followed by the names of the packages you want to install.

### The packages you can install

Currently these are:

* cvi-pinmux-cv181x
* firmware-vcodec-cv181x

...and board-specific packages like:

* cvitek-fsbl-licheervnano
* cvitek-middleware-licheervnano
* cvitek-osdrv-licheervnano-kvm
* device-key-licheervnano
* duo-pinmux-duo256
* gadget-nic-licheervnano
* linux-image-licheervnano-kvm
* load-systemko-licheervnano
* nanokvm-licheervnano
* sensor-config-licheervnano

## How to contribute?

Please contribute changes and bug reports in the relevant repository above.

Have a issue? Please create a
[issue on this repository](https://github.com/Pairman/sophgo-sg200x-debian/issues)

Have your own enhancements or bug fixes? Please create a 
[pull request on this repository](https://github.com/Pairman/sophgo-sg200x-debian/pulls).

## Thanks

[scpcom/sophgo-sg200x-debian](https://github.com/scpcom/sophgo-sg200x-debian)
[scpcom/scpcom.github.io](https://github.com/scpcom/scpcom.github.io)
[Fishwaldo/sophgo-sg200x-debian](https://github.com/Fishwaldo/sophgo-sg200x-debian)  
[Fishwaldo/sophgo-sg200x-packages](https://github.com/Fishwaldo/sophgo-sg200x-packages)
