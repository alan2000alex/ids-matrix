[![Build Status](https://img.shields.io/travis/realaravinth/ids-matrix.svg?style=flat-square)](https://travis-ci.org/realaravinth/ids-matrix)
[![License](https://img.shields.io/badge/License-Apache%202.0-yellowgreen.svg?style=flat-square)](https://opensource.org/licenses/Apache-2.0)

# ids-matrix
A lightweight Intrusion Detection System built on top of matrix
<br><br>
**WARNING: `realaravinth/ids-matrix` comes with ABSOLUTELY NO WARRANY, to the extent permitted by applicable law.**
<br><br>
The instructions provided here are for the Debian(Buster) GNU/Linux, however it can be modified to work with other distrubtions as well.
It uses `pam_exec` to collect login information so kindly refer to your distribution's guide if this guide doesn't work.

## Table of contents:

- [Dependencies:](#dependencies)
- [How to compile](#how-to-compile)
- [Installation](#installation)
- [Contributions](#contributions)

## Dependencies

  * libpam-modules
  * coreutils(uses `date` and `uname`)[optional]
  * net-tools(uses `hostname`)[optional]<br>
  * rust(to compile)
  *optional: you can remove parts of the code if you wish to not to install the optional dependencies*

## How to compile

  1. `cd` into source directory
  2. edit src/main.rs and fill
    * `server`: url of your matrix server
    * `access_token`: access token of your matrix account(create new one with least priveleges)
    * `room_id`: room ID of the room where you want to publish the updates
  3. `cargo build --release`
    This compiles the program and places the binary in `target/release` directory

## Installation
  
  1. Place `ids-matrix` and `notify.sh` binary in `/usr/local/bin` of your server and give executable priveleges
  2. Append the following to `/etc/pam.d/sshd`(always take backup of the original config):
    `session optional pam_exec.so /usr/local/bin/notify.sh`
    
## Contributions
Yes please! Fork this repo and send in PRs, I'll be happy to review and merge them!
 
    
