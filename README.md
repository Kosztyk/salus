![icon@2x](https://github.com/user-attachments/assets/61c52769-9e92-43cb-b9ea-66ac353db157) 

Home-Assistant Custom Components
Custom Components for Home-Assistant (http://www.home-assistant.io)

# Salus Thermostat Climate Component
My device is RT301i, it is working with it500 thermostat, the ideea is simple if you have a Salus Thermostat and you are able to login to salus-it500.com and controll it from this page, this custom component should work.
Component to interface with the salus-it500.com.
It reads the Current Temperature, Set Temperature, Current HVAC Mode, Current Relay Mode.

Keep in mind this is my first custom component and this is also the first version of this Salusfy so it can have bugs. Sorry for that.

**** This is not an official integration.
### Installation
* If not exist, in config/custom_components/ create a directory called salusfy 
* Copy all files in salusfy to your config/custom_components/salusfy/ directory.
* Configure with config below.
* Restart Home-Assistant.

### Usage
To use this component in your installation, add the following to your configuration.yaml file:

### Example configuration.yaml entry

```
climate:
  - platform: salusfy
    username: "EMAIL"
    password: "PASSWORD"
    id: "DEVICEID"
```
![image](https://user-images.githubusercontent.com/33951255/140300295-4915a18f-f5d4-4957-b513-59d7736cc52a.png)
![image](https://user-images.githubusercontent.com/33951255/140303472-fd38b9e4-5c33-408f-afef-25547c39551c.png)


### Getting the DEVICEID
1. Loggin to https://salus-it500.com with email and password used in the mobile app(in my case RT301i)
2. Click on the device
3. In the next page you will be able to see the device ID in the page URL
4. Copy the device ID from the URL
![image](https://user-images.githubusercontent.com/33951255/140301260-151b6af9-dbc4-4e90-a14e-29018fe2e482.png)


### Known issues
salus-it500.com server is bloking the IP of the host, in our case the HA external IP. This can be fixed with router restart in case of PPOE connection or you can try to send a mail to salus support...

### Added GUI setup steps 

<img width="1374" alt="Screenshot 2025-01-21 at 22 35 54" src="https://github.com/user-attachments/assets/6474ced8-b990-4cb0-b260-dfff336739ee" />
### Added sensors in the integration 

<img width="1013" alt="Screenshot 2025-01-22 at 01 57 30" src="https://github.com/user-attachments/assets/a556d699-1d63-4afe-8e2d-1dbf1fd79f1a" />

Example of card:


<img width="479" alt="Screenshot 2025-01-22 at 02 01 09" src="https://github.com/user-attachments/assets/b62d74d1-fac8-4894-90fb-73ede770da0b" />




type: horizontal-stack
cards:
  - type: entities
    entities:
      - entity: sensor.heating_time
      - entity: sensor.heater_history
      - entity: sensor.yesterday_heater_history
      - entity: sensor.thermostat_state
title: Heating Statistics

Note: Sensor statistics will be lost at HA restart, is an known issue, did not found a solution yet, any help here will be apreciated.
      Thanks to Serban Iliuță that shared with us the sensor codes.
