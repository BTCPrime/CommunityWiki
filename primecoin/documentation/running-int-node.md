<!-- TITLE: Running Int Node -->
<!-- SUBTITLE: A quick summary of Running Int Node -->

A node to act as an bridge between primecoin core and primecoin-ng-core. @eXtremal has built a binary for Ubuntu 17.10, so,

Here's how to set one up;


Sign up to DigitalOcean and Build an Ubuntu 17.10 Box, $10 level should be sufficient;

https://m.do.co/c/0ebcae270748

You will be emailed the login password.



Log in as root;

ssh root@whatever
create a new password

Create a user to run the node;

```
adduser primecoin
```

Add the user to Sudo;

```
usermod -aG sudo primecoin
```

switch to this user;

```
su - primecoin
```

Install pre-reqs;

```
sudo apt-get update
sudo apt-get install libboost-all-dev
sudo apt-get install libdb5.3++
sudo apt-get install libminiupnpc10
sudo apt-get install unzip

```

Download the primecoind executable and make it executable;

```
wget https://primecommunity.org/files/primecoind.bin
sudo chmod u+x primecoind.bin

```


Execute primecoind once;

```
./primecoind
```

You will get a message about setting an rpc user and password, so follow the instructions.

```
nano /home/primecoin/.primecoin/primecoin.conf
```

And paste your username and password into that file.

Download and extract the blockchain snapshot;

```
wget https://primecommunity.org/files/primecoin_blockchain.zip
unzip primecoin_blockchain.zip -d ~/.primecoin
(Overwrite [A]ll when prompted)

```

Open up the firewall port;

```
sudo ufw allow 9911
```

And finally;


start primecoind

```
./primecoind.bin --daemon
```

Check primecoind is running;

```
./primecoind.bin getinfo

```