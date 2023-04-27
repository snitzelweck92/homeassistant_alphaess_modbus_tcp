# Integrate a ALPHAESS System to Home Assistant
## Introduction
Since March 2023 we have at home a PV-System from AlphaESS.\
Since years I'm using Home Assistant for my smarthome and tracking of all my entities in my home.\
So the idea was to integrate the AlphaESS system to HomeAssistant. \
The official API was not enough, the other solutions are interesting, but my Software-Developer-Heart says:\
"There is a MODBUS TCP interface, this must be usable". \
From now on, I tried to integrate the system with modbus. \
And it is working :)

## Compatibilty
:white_check_mark: Modbus-TCP connection\
:white_check_mark: AlphaESS Smile Hi10 with 7,8kWh battery

## Features
:white_check_mark: Connection to the Inverter via Modbus TCP\
:white_check_mark: Setup of sensor entities inside of Home Assistant \
:white_check_mark: Setup of a automation and the helpers for setting the "Max Feed to Grid - Rate" (How many energy is given to the grid)\
:white_check_mark: Setup of template-sensor to provide the values to the energy dashboard\
:white_check_mark: Open for modifications, no integration or other complicated stuff. Simply YAML-file!\
:white_check_mark: No additional integrations or AddOns needed

## Prerequisites
- Home Assistant v2023.1 or greater
- compatible AlphaESS-System with Modbus-TCP interface --> See instructions of your System

## Installation
- Download the YAML-file
- Copy *`integration_alpha_ess.yaml`* into the folder which is used for packages inside of you HomeAssistant-Enviroment (e.g. folder "packages", is no packages already included in your *`configuration.yaml`* create a folder with the name "packages" in you config-folder)
- Include this folder inside of your *`configuration.yaml`* with following lines
  ```
  homeassistant:
    packages: !include_dir_named packages
  ```
  **NOTE: "packages" is the name of the folder you created or already using!**
- Setup the following values in your *`secrets.yaml`*
  ```
  alphaess_modbus_host_ip: 192.168.178.104 #TODO: Set ip adress of Alpha Ess Storage system
  alphaess_modbus_host_port: 502 #Set port of Alpha Ess system - default: 502
  alphaess_modbus_slaveId: 85 #Set slaveId of Alpha Ess system - default: 85
  ```
- Check your configuration under the developer-tools
- Perform a restart of your HomeAssistant

## Usage
- You will find your entities in the overview
- For description of the entities, check the file *`integration_alpha_ess.yaml`*, the comments should be the explanation

## Links
- Description of ModbusTCP from AlphaESS:\
https://www.alpha-ess.de/images/downloads/handbuecher/AlphaESS-Handbuch_SMILE_ModBus_RTU_TCP_V21.pdf (german)
- List of Modbus-Registers:\
https://www.alpha-ess.de/images/downloads/handbuecher/AlphaESS_Register_Parameter_List.pdf (german)

## WARNINGS
- **Everything what is provided here is without a guarantee!**
- **No support is promised by my side, i will help you, if i can!**
- **Please be patient with writing registers, it can destroy your system!**
- **Note, that only the Smile-Hi10-System is tested!**
- **When there is a damage on your system, or you are loosing your guarantee, this is your problem. You are using this helper on your own risk!**
