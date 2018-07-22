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

Now that we have everything set, we can install homebridge globally with some unsafe parameter to avoid some nasty errors regarding permissions. As seen in https://github.com/nfarina/homebridge/wiki/Running-HomeBridge-on-a-Raspberry-Pi:
```
sudo npm install -g --unsafe-perm homebridge hap-nodejs node-gyp
# random error
# npm WARN notice [SECURITY] hoek has the following vulnerability: 1 moderate. Go here for more details: https://nodesecurity.io/advisories?search=hoek&version=2.16.3 - Run `npm i npm@latest -g` to upgrade your npm version, and then `npm audit` to get more info.

```

And time to run `homebridge`. That will fail because it cannot find a `config.json` file
```
/opt/nodejs/bin/homebridge
```
