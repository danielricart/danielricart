Why not pushing custom data to Apple Homekit?
Like the information I got from my DHT11.

There's a nice piece of OpenSource software called "Homebridge" that acts as a sensors hub. It has several plugins to read from different home devices. One of them allows to push information to Apple Homekit and have it available using the "Home" app.

It is based on nodejs. Raspberry's nodeJS is quite old (4.8.2 at the moment of writing) while the latest version now is 10, released in April and potentialy an LTS version.

So, there's this nice script that installs for us the latest version. See https://github.com/audstanley/NodeJs-Raspberry-Pi to get some more information.
```wget -O - https://raw.githubusercontent.com/audstanley/NodeJs-Raspberry-Pi/master/Install-Node.sh | sudo bash
node -v
``
Now we have nodeJs version 10.5.0 at least. 
