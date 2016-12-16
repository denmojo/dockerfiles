docker zcash
=============

This project builds a Docker image with zcash v1.0.4.

## Pre-requisites
  * Docker

## Building
  * `docker build -t zcash .`

You can also pull it from Docker Hub:
  * `docker pull denmojo/zcash`

## Configuration
  * `docker run --name zcash -ti zcash /bin/zsh`

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

## Running zcash
  * `~/zcash/src/zcashd` 

## Interacting with zcashd
  * `docker exec -ti zcash /root/zcash/src/zcash-cli -help`
