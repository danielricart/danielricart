Why not pushing custom data to Apple Homekit?
Like the information I got from my DHT11.

There's a nice piece of OpenSource software called "Homebridge" that acts as a sensors hub. It has several plugins to read from different home devices. One of them allows to push information to Apple Homekit and have it available using the "Home" app.

It is based on nodejs. Raspberry's nodeJS is quite old (4.8.2 at the moment of writing) while the latest version now is 10, released in April and potentialy an LTS version. We will use current LTS NodeJS 8.11.3.

So, there's this nice script that installs for us the latest version. See https://github.com/audstanley/NodeJs-Raspberry-Pi to get some more information.
```
wget -O Install-Node.sh https://raw.githubusercontent.com/audstanley/NodeJs-Raspberry-Pi/master/Install-Node.sh
sudo bash Install-Node.sh 
sudo install-node -v 8.11.3
node -v
```
Now we have nodeJs version 8.11.3 at least. 

```
# Linux-only (does not apply to mac setups)
# random dependency
sudo apt-get install -y libavahi-compat-libdnssd-dev
```

Now that we have everything set, we can install homebridge globally with some unsafe parameter to avoid some nasty errors regarding permissions. As seen in https://github.com/nfarina/homebridge/wiki/Running-HomeBridge-on-a-Raspberry-Pi .
As you will notice, most of the nodejs commands are run as `root` allowing unsafe actions on the system. This is quite required because of the nature of Homebridge. It is not ideal but as a long as our system is safe and secure we are fine.

```
sudo npm install -g --unsafe-perm homebridge hap-nodejs node-gyp
# update NPM
npm i npm@latest -g --unsafe-perm
cd /opt/nodejs/lib/node_modules/homebridge/
sudo npm install --unsafe-perm bignum
# unused commands, AFAIK.
# cd /opt/nodejs/lib/node_modules/hap-nodejs/node_modules/multicase-dns
# sudo PATH="$PATH:/opt/nodejs/lib/node_modules/npm/bin/node-gyp-bin:/opt/node/bin" node-gyp BUILDTYPE=Release rebuild
```
Add homebdrige to a more friendly location:
```
sudo ln -s /opt/nodejs/lib/node_modules/homebridge/bin/homebridge /usr/bin/homebridge
```
And time to run `homebridge`. 
```
homebridge
```
pi@raspberrypi:~ $ homebridge
[2018-7-22 11:15:01] config.json (/home/pi/.homebridge/config.json) not found.
[2018-7-22 11:15:01] No plugins found. See the README for information on installing plugins.
Setup Payload:
X-HM://0023XXXY1ZZZ
Scan this code with your HomeKit app on your iOS device to pair with Homebridge:

[HERE YOU WILL SEE A QR CODE]

Or enter this code with your HomeKit app on your iOS device to pair with Homebridge:

    ┌────────────┐
    │ 012-12-123 │
    └────────────┘

[2018-7-22 11:15:02] Homebridge is running on port 38125.

