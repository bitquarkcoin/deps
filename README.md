# Pre-compiled deps for Gitian Cross-compiling Win32 client on Ubuntu 14.04
Just follow these simple steps 

# First, install dependencies:
'sudo apt-get install apache2 git apt-cacher-ng python-vm-builder qemu-kvm ruby qemu-utils rubygems zip curl'

# Sanity checks:
'sudo service apt-cacher-ng status'   # Should return apt-cacher-ng is running
'ls -l /dev/kvm'   # Should show a /dev/kvm device

# Clone local copies of BitQuark, Pre-compiled Deps, and Gitian source-codes
Enter Ubuntu terminal
'cd ~'
'git clone git://github.com/bitquarkcoin/BitQuark-0.8.3r20.git bitquark'
'git clone git://github.com/devrandom/gitian-builder.git gitian'
'cd gitian'
'git clone https://github.com/bitquarkcoin/deps.git inputs'
'zip -r inputs/bitquark-0.8.3.20.zip ../bitquark'

# Build Base Virtual Machine (this will take some time so do not quit prematurely)
sudo bin/make-base-vm --arch i386

# Build BitQuark Windows Client
sudo bin/gbuild ../bitquark/contrib/gitian-descriptors/gitian-win32.yml

## The compiled Windows GUI client, daemon and Windows Installer binaries (along with the source-code) will output to gitian/build/out.
