# Void User Repository (VUR)

This repository contains a custom XBPS source packages collection for the Void Linux distribution.

See [void-linux/void-packages](https://github.com/void-linux/void-packages) for details.

## Table of Contents

- [Packages](#packages)
- [Installing](#installing)
    - [Automatic](#automatic)
    - [Manual](#manual)
- [Building](#building)

## Packages

- looking-glass
    - looking-glass-dkms
    - looking-glass-obs
- vesktop

## Installing

> [!NOTE]
> Repository is maintained by GitHub Actions.

### Automatic

Add this repository:

```
# echo 'repository=https://github.com/Wiylan/VUR/releases/latest/download' > /etc/xbps.d/vur.conf
```

To install a package:

```
# xbps-install --sync <pkgname>
```

### Manual

Add the package to your local repository:

```
$ xbps-rindex --add <pkgname>-<version>_<revision>.<arch>.xbps
```

To install the package:

```
# xbps-install --repository $PWD <pkgname>
```

## Building

Clone this git repository:

```
$ git clone --single-branch --branch main https://github.com/Wiylan/VUR.git custom
```

Clone the `void-linux/void-packages` git repository:

```
$ git clone https://github.com/void-linux/void-packages.git
```

Copy the custom `srcpkgs`:

```
$ cp --recursive custom/srcpkgs void-packages
```

Install the bootstrap packages:

```
$ cd void-packages
$ ./xbps-src binary-bootstrap
```

Build a package:

```
$ ./xbps-src pkg <pkgname>
```

Once built, the package will be available in `hostdir/binpkgs`.
To install the package:

```
# xbps-install --repository hostdir/binpkgs <pkgname>
```
