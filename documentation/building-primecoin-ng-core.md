<!-- TITLE: Building Primecoin Ng Core -->
<!-- SUBTITLE: A quick summary of Building Primecoin Ng Core -->

# Building an XPM-NG-Core Testnet Node

Ubuntu 18.04 3gb RAM


### Install Dependancies


```
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3

sudo apt-get install software-properties-common

sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev
```


### Need Old LibSSL

```

sudo apt-get install libssl1.0-dev

```

### Clone the Repo

```

git clone https://github.com/primecoin-ng-group/primecoin-core.git
```


### Set up BerkeleyDb 4

```
mkdir primecoin-core/db4/
wget 'http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz'
tar -xzvf db-4.8.30.NC.tar.gz
../dist/configure --enable-cxx --disable-shared --with-pic --prefix=/<user>/primecoin-core/db4/
```

### Build
```
cd ~/primecoin-core
./autogen.sh
./configure LDFLAGS="-L/<user>/primecoin-core/db4/lib/" CPPFLAGS="-I/<user>/primecoin-core/db4/include/"

make -s -j5

```

### Configure

```
touch ~/.bitcoin/bitcoin.conf
nano ~/.bitcoin/bitcoin.conf
```

Add following config; 

```
seednode=primeseedtn.muuttuja.org
rpcuser=primecoin
rpcpassword=<create password>
rpcport=9914
stdinrpcpass=<create password>
txindex=1
listen=1
testnet=1
```

### Start the node; 

```
./primecoin-core/src/bitcoind --daemon


Add the following node to speed up sync; 

 ./primecoin-core/src/bitcoin-cli addnode coinsforall.io add
```

### Check the sync

Should take around 1-2 hours to sync up. 

```
 ./primecoin-core/src/bitcoin-cli getblockchaininfo
 ```