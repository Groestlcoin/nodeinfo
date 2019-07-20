## NodeInfo

Simple QT fullscreen app compatible with linuxfb (direct framebuffer) that displays information about a Groestlcoin Node


### Compile

Debian / Ubuntu

    sudo apt-get install build-essential libtool autotools-dev automake pkg-config
    sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools

    ./autogen.sh
    ./configure
    make

OSX

    brew install automake libtool pkg-config qt

    ./autogen.sh
    ./configure
    make


### Run

X11/OSX

    GROESTLCOIN_CLI=/path/to/bin/groestlcoin-cli ./nodeinfo

Regtest Linux Without X11 direct framebuffer

    GROESTLCOIN_CLI=/grs/apps/groestlcoin-2.17.2/bin/groestlcoin-cli ./nodeinfo -platform linuxfb

Mainnet custom Datadir Linux Without X11 direct framebuffer

    GROESTLCOIN_ARGS="-datadir=/grs/data/groestlcoin" GROESTLCOIN_CLI=/grs/apps/groestlcoin-2.17.2/bin/groestlcoin-cli ./nodeinfo -platform linuxfb

**Make sure your user is in the group `tty` if you run with `-platform linuxfb` via SSH or other no direct tty ways.**

#### Configuration Options

Show GRS exchange rate:

* NodeInfo will look for a file called `exchangerate`
* The file should contain a float without "," or "'" (example: `5000.00`,... but NOT `5'000.00` and NOT `5000,00`)
* It's possible to set the currency code by adding the text after a comma "," (example: `5000.00,CHF`   results in `GRS/CHF 5000.00`)
* It's possible to set the complete text adding a third element (example: `5000.00,CHF,BLA`    results in `BLA 5000.00 [second element is ignored])

Environment Variables

* `GROESTLCOIN_CLI` path to the groestlcoin-cli binary
* `GROESTLCOIN_ARGS` arguments to padd to the groestlcoin-cli (example: `-regtest -datadir = /tmp/dummy`)
* `GROESTLCOIN_RPC_TIMEOUT` the shell-pipe call timeout
* `NODE_INFO_EXCHANGE_RATE_FILE` path to the exchangerate file
* `WINDOWED` if set to `1`, nodeinfo will run in a window (not compatible with the `linuxfd` platform)
