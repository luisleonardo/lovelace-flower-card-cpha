

## This component is deprecated. Please use this one instead: https://github.com/Olen/lovelace-flower-card




# lovelace-flower-card-cpha

*This is a Lovelace flower card for Home Assistant that won't break if with sensors without conductivity attribute (battery will be used if there's no conductivity attribute). The code is based on the original card by [thomasloven](https://github.com/thomasloven/lovelace-flower-card) and some random code found in the [Home Assistant forums](https://community.home-assistant.io/).*

![](https://github.com/luisleonardo/-lovelace-flower-card-cpha/raw/main/lovelace-flower-card-example.png)



## Dependencies

1. lovelace-card-tools (https://github.com/thomasloven/lovelace-card-tools)
2. OpenPlantbook-client (https://github.com/slaxor505/OpenPlantbook-client)
3. Plant images (https://we.tl/t-baN733EttD)



## Instructions

### Card installation

##### 1: Copy all files

- Copy the file `flower-card-cpha.js` to `www/lovelace-flower-card-cpha/`

- Unzip and copy all plant images to `www/images/plants/`



##### 2: Add the card to the Lovelace Dashboard

- Go to "Configuration -> Lovelace Dashboards -> Resources"

- Press "+ add resource" in the lower right corner
- Add the following:
  - URL: `/local/lovelace-flower-card-cpha/flower-card-cpha.js`
  - Resource type: `JavaScript Module`



### Plant Configuration

##### 1. Separate plants from the configuration file *(not mandatory, but recommended)*:

- Edit your "configuration.yaml" file and add the following line:
  ```plant: !include plants.yaml```

- Create a "plants.yaml" file



##### 2. Edit your plant configuration file:

- Edit your "plants.yaml" (or "configuration.yaml" if you skipped the previous step) and create a config with your openplantbook credentials, plants and sensors like in the example bellow.
- If your sensor does not have a conductivity attribute, remove that line and the card will use the battery attribute.

```
openplantbook:
  client_id: 'SUPER_SECRET_CLIENT_ID'
  secret: 'SUPER_SECRET_CODE'
  
monstera_deliciosa:
  species: monstera deliciosa
  name: Monstera
  sensors:
    moisture: sensor.moisture_flower_sensor
    battery: sensor.battery_flower_sensor
    temperature: sensor.temperature_flower_sensor
    conductivity: sensor.conductivity_flower_sensor
    brightness: sensor.illuminance_flower_sensor

alocasia_cucullata:
  species: alocasia cucullata
  name: Alocasia
  [...]
```



### Card Configuration

##### 1. Add plants to Lovelace:

Manually create your cards with the type `custom:flower-card-cpha`. Here's an example:

```yaml
type: custom:flower-card-cpha
entity: plant.monstera_deliciosa
```
