# Mining with Parity 

Parity is designed to be fully compatible with `ethminer`. If you're already using a combination of `geth` and `ethminer` then you'll find mining with Parity very familiar.

First get a Parity node up and running (either build yourself or install one of the packages; the [[Quick-start]] guide can help you). Next, you'll need to install `ethminer`.

### Rolling your own

There are packages built for various platforms, though if all else fails, you can just build it straight from the main repository:

```
git clone https://github.com/ethereum/cpp-ethereum
cd cpp-ethereum
mkdir build
cd build
cmake -DBUNDLE=miner ..
```

`ethminer` can be found in the `libethereum/ethminer` directory; you'll probably want to copy it to somewhere in your `$PATH`.

### Ubuntu

To install `ethminer` on Ubuntu, you can use the package manager:

```
sudo add-apt-repository ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethminer
```

### Mac OS X Homebrew

TODO

## Starting it

Once you have a synced Parity node running the JSONRPC interface, you'll be able to mine with `ethminer`. You'll probably want to set the destination address (where the rewards go). If you have an address already, great. If you don't, then you can make one in Parity with:

```
parity address new
```

You'll be asked for a password and be given an address. Once done, you should run parity and tell it to mine to that address when required. Supposing your address is `0037a6b811ffeb6e072da21179d11b1406371c63`, then you would run:

```
parity --author 0037a6b811ffeb6e072da21179d11b1406371c63 -j
```

Once Parity is running and synced, running `ethminer` with work without any further configuration. e.g. run `ethminer -G --opencl-device 0` to GPU mine on the first OpenCL device found.