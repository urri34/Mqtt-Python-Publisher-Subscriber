# HA-Mqtt-Python-Publisher-Subscriber
Contains the python scripts I use to interact with a Mqtt server. There is a publisher one and a subscriptor one. All the configuration parameters are in the configuration.py file.

## configuration.py:
### Basic configuracion options:
- Broker = '192.168.1.11'

Basically the ip address or the name of your Mqtt broker. If your are playing around with a HAServer (probably with the Mosquito broker) it's the ip address of the server it's self.
  
- UserName = 'mqtt'

The username used to connect to the Mqtt broker. If your are playing around with a HAServer it can be any of the users that have access to the HA Server (it can be a good idea to use the same one you configured while setting up the Mosquito Mqtt broker in HAServer).

- Password = 'mqtt'

The password for the username

- Topic = "display/state"

The topic under which is going to be published the messages in our Mqtt broker. In my case it's part of a bigger project.

### Extended configuracion options:
- LogToFile = 1
- LogFile=path.dirname(__file__).replace('\\','/')+'/Mqtt_Pub_Subs.log'
- LogLevel=DEBUG # It can be DEBUG INFO WARNING ERROR CRITICAL
- Port = 1883
- ClientId = f'python-mqtt-pub-{randint(0, 1000)}' # Just some value in order to appear in the logs
- RetryConnectionTime = 5
- PublishRepetitionTime = 10
- WaitForLoopTime = 1

It's not really necessary to configure any of this parameters, and their names have to be clear enough in order to know what are the used to. Just one to consider: WaitForLoopTime, dont try to push it to 0, it seems stupid but it takes sometime to construcs the loop and it's the best option I found in order to wait for it.

## publish.py
```sh
python .\publish.py
[2024-01-17 08:02:19,918] DEBUG    publish.py   main(): Logging active for me: publish.py
```

![Figure1](Figure_1.png)

## subscribe.py
```sh
python .\subscribe.py
[2024-01-17 08:02:19,918] DEBUG    publish.py   main(): Logging active for me: publish.py
```

![Figure2](Figure_2.png)

## Mqtt explorers:
Mqtt explorer is a very good option in order to be able to see in real time how our messages are being stored in Mqtt. Thanks to Thomas Nordquist! 

https://github.com/thomasnordquist/MQTT-Explorer
