<div align="center">
    <h1>makedeb</h1>
    <img height="150" src="https://dl.uploadgram.me/6119617f89775h?raw">
</div>

## Overview
makedeb takes PKGBUILD files and creates Debian packages installable with APT

## Depends: 

    sudo apt install -y bash binutils file dpkg-dev makepkg

## Setup:

**Repository Configuration**

First, add the signing key:

    wget -qO - 'https://proget.hunterwittenborn.com/debian-feeds/makedeb.pub' | gpg --dearmor | sudo tee /usr/share/keyrings/makedeb-archive-keyring.gpg &> /dev/null

Next, add the repository information to your system:

    echo 'deb [signed-by=/usr/share/keyrings/makedeb-archive-keyring.gpg arch=all] https://proget.hunterwittenborn.com/ makedeb main' | sudo tee /etc/apt/sources.list.d/makedeb.list

Lastly, update the repository cache on your system:

    sudo apt update

The stable release is downloadable from the `makedeb` package:

    sudo apt install makedeb

## Options:

      -A, --ignore-arch        Ignore errors about mismatching architectures
      -d, --nodeps             Skip all dependency checks
      -F, --file, -p           Specify a build file other than 'PKGBUILD'
      -h, --help               Show this help menu and exit
      -H, --field              Append the resulting control file with custom fields
      -i, --install            Automatically install package(s) after building
      -Q, --no-fields          Skip adding values from 'control_fields' variable in PKGBUILD to control file
      -v, --distro-packages    Source package relationships from distro-specific variables when they exist
      -V, --version            Print version information and exit
      -r, --rmdeps             Remove installed dependencies after building
      -s, --syncdeps           Install missing dependencies
      --verbose                Print (very) detailed logging

The following options can be passed to makepkg:
 
      --printsrcinfo           Print a generated .SRCINFO file and exit
      --skippgpcheck           Do not verify source files against PGP signatures

