### How to Install Node and NPM on VPS Hosting Remote Server
#
- Get Access to Remote Server via SSH
```sh
Syntax:- ssh -p PORT USERNAME@HOSTIP
Example:- ssh -p 22 raj@216.32.44.12
```
- Check if Node and NPM already Installed
```sh
node -v
npm -v
```
- Install Node and npm
```sh
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```
- You can get Latest Version of Node and NPM Installtion Link by following official 
https://github.com/nodesource/distributions/blob/master/README.md


- Installed NVM Package 

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash

Close and reopen your terminal or run source ~/.bashrc 
-Check list all the node version
nvm list-remote

-Install the any node version 
nvm install 14.17.0

-Select that version to use 
nvm use X.XX.X

