# ESP32_8266-environment-controls

Utilizing the ESP32_8266 microcontroller, the goal is to monitor environmentals (temp, humidity) for v1 of project
REQ: Node_RED and MQTT are installed.  

find Node JS version.. in my case im using v20    
    terminal:  sudo apt-get install -y nodejs build-essential

Confirmed with command:
    terminal: nodejs --version
    terminal: nodejs -v    (works also) 

Node-RED will need to be installed Globally, makes it easier to access and run Node.js
run the following cmd   
    Terminal: sudo npm install -g --unsafe-pem node-red

    -g is global
    --unsafe-perm tells npm to not set --user or --group to root while running
    node-red is the package that NPM is installing
    
-- if you get any errors, try cmd with "sudo"

to run Node-Red 
Terminal: node-red

Accessing Node-Red:
usually its http://localhost:1880   or http://serverip:1880

         if you have firewall ... disable it or set an allow rule for port 1880

--- to run a without persistence or systemd use the above.

to add node-red as a service - 

    sudo nano /etc/systemd/system/node-red.service

add the following content:

    [Unit]
    Description=Node-RED
    After=network.target

    [Service]
    ExecStart=/usr/bin/node-red
    Restart=on-failure
    KillSignal=SIGINT

    [Install]
    WantedBy=multi-user.target


--------- save the file
then run in terminal:
sudo systemctl daemon-reload

--------- start node-red and enable on boot
sudo systemctl start node-red
sudo systemctl enable node-red


--------- you have the option to add encrypted communications for your install
        find the required node.js settings
