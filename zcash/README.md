docker zcash
=============

This project builds a Docker image with zcashd.

## Pre-requisites
  * Docker

## Building
  * `docker build -t zcash .`

You can also pull it from Docker Hub:
  * `docker pull denmojo/zcash`

## Configuration

Make a settings file (the following is for testnet):
```
mkdir ~/.zcash/  
cd ~/.zcash/

echo testnet=1 > zcash.conf  
echo addnode=testnet.z.cash >> zcash.conf  
echo rpcuser=username >> zcash.conf  
echo rpcpassword=$(head -c 32 /dev/urandom | base64) >> zcash.conf 
```

Use the following for mainnet (live production network):
```
mkdir ~/.zcash/  

echo "addnode=mainnet.z.cash" >~/.zcash/zcash.conf
echo "rpcuser=username" >>~/.zcash/zcash.conf
echo "rpcpassword=`head -c 32 /dev/urandom | base64`" >>~/.zcash/zcash.conf
```

```
e.g. in macOS:
add in there any configurations such as gen=1 to enable CPU mining
```

## Running zcash
  * `docker run -v /Users/<whoever>/.zcash:/root/.zcash --name zcashd --rm -ti zcash` 

## Interacting with zcashd
  * `docker exec -ti zcash /root/zcash/src/zcash-cli -help`

It might be helpful to set up aliases in your .bashrc or .zshrc
```
alias zcashd='docker run -v /Users/<whoever>/.zcash:/root/.zcash --name zcashd --rm -ti zcash'
alias zcash-cli='docker exec -ti zcash /root/zcash/src/zcash-cli'
```

This allows you to just run zcash as if it were local.
