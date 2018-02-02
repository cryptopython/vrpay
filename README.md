# VRPay
VRPay is a proof-of-work/proof-of-stake currency designed to allow participants in virtual reality space to pay each other for goods and services in real time.  It has a short block time of about 5 minutes to allow for quick transactions.

VRPay can be mined with a CPU

The rewards start out at 60000 VRP per block and decline gradually to block 30000 where it switches to proof-of-stake. 

The premined coins in the genesis block will be used to fund development in the
form of code bounties.

# Build Instructions

Skip here for [OS X Build Instructions](#os-x-build-instructions)

1. Install the pre-requisites

```
sudo apt-get install build-essential libssl-dev libdb-dev libdb++-dev libboost-all-dev git libssl1.0.0-dbg libdb-dev libdb++-dev libboost-all-dev libminiupnpc-dev libminiupnpc-dev libevent-dev libcrypto++-dev libgmp3-dev libminiupnpc-dev
```

2. Build the daemon

```
cd src
make RELEASE=1
```

3. Install it

```
sudo make install
``` 

4.  create a ~/.vrpay/vrpay.conf file with the following: 
```
rpcuser=user
rpcpassword=x
rpcallowip=*
daemon=1
server=1
txindex=1
gen=0
```

5. Run it
```
nohup /usr/sbin/vrpayd &
```

Save the ```~/.vrpay/wallet.dat``` file as a backup

6. Mine your coins using the official mining pool (recommended)

```
minerd -o stratum+tcp://pool.bgpcoin.com:3008/ -u `bgpcoind getaccountaddress 0` -p x
```

-or-

7. Mine your coins (On localhost using all threads)

```
minerd -o http://127.0.0.1:32076 -u user -p x
```

-or-

8. Mine your coins (On localhost using one thread)
```
minerd -t 1 -o http://127.0.0.1:32076 -u user -p x
```

Enjoy!

# OS X Build Instructions (High Sierra 10.13 only for now)

1. Install the pre-requisites

```
brew install automake berkeley-db4 libtool boost --c++11 miniupnpc  \
        openssl pkg-config homebrew/versions/protobuf260 --c++11 \
        qt5 libevent mongodb berkeley-db4 libtool boost@1.57 miniupnpc \
        openssl pkg-config protobuf python \

brew link boost@1.57 --force
```

2. Build the daemon

```
cd bgpcoin/src/leveldb
make clean && make -j && make -j memenv_test
cd ..
make -f makefile.osx -j RELEASE=1
```

3. Install it
```
sudo make install
```

4.  create a ~/.bgpcoin/bgpcoin.conf file with the following: 
```
rpcuser=user
rpcpassword=x
rpcallowip=*
daemon=1
server=1
txindex=1
gen=0
```

5. Run it
```
nohup /usr/sbin/bgpcoind &
```

Save the ```~/.bgpcoin/wallet.dat``` file and you can load it with your QT wallet

6. Mine your coins using the official mining pool (recommended)

```
minerd -o stratum+tcp://pool.bgpcoin.com:3008/ -u `bgpcoind getaccountaddress 0` -p x
```

-or-

7. Mine your coins (On localhost using all threads)

```
minerd -o http://127.0.0.1:32076 -u user -p x
```

-or-

8. Mine your coins (On localhost using one thread)
```
minerd -t 1 -o http://127.0.0.1:32076 -u user -p x
```

Enjoy it Mac style

# Current Bounties

1. 8 BGP per blog post evangelizing BGPCoin
2. 1024 BGP (4 block rewards) for a cleaner Makefile that integrates with systemd
3. 10240 BGP (40 block rewards) for a nicely designed site
4. 10240 BGP (40 block rewards) for command line scripts that allow ISPs to pay each other using the API
5. 20480 BGP (80 block rewards) for an ISP who agrees to take BGPCoin
6. 20480 BGP (80 block rewards) for a Mac OS X wallet
7. 20480 BGP (80 block rewards) for an Android wallet
8. 102400 BGP (400 block rewards) for listing on an exchange, per exchange
