# c14_rpi_svxlink_if
Raspberry Pi Hat for SVXLink

This repository contains the code and instructions for a custom interface between radio transceivers and a Raspberry Pi running SVXLink.

## Repository contents
The repository contains the following files and directories:

* c14_rpi_svxlink_if.kicad_pcb: the KiCAD project for the custom PCB design.
* LICENSE: the license file for the repository (CC-BY-SA).
* README.md: this file.

![image](https://user-images.githubusercontent.com/1631996/226144165-9e673233-b85d-437a-a232-d62e1d56a006.png)

## Features

The interface offers the following features:

* Generic DB9 connector for interfacing to transceiver(s)
* Isolated audio rx/tx and signal paths (PTT, Squelch)
* Audio levels can be set with potis
* Fan control output and tacho input
* Telemetry inputs:
  * ADS1115 ADC (i.e. for voltage or RSSI measurement)
  * I2C connectors (i.e. for temperature sensors)

We deliberately decided against placing a soundcard IC on the interface. We use an external, generic USB soundcard instead, as these type of soundcards are very easy and cheap to get on various market places.

## Signal mapping

### DB9 Connector

| Number | Name       |
| ------ | ---------- |
| 1      | SQL_DET-   |
| 2      | SQL_DET+   |
| 3      | RSSI       |
| 4      | RX_AUDIO- |
| 5      | RX_AUDIO+ |
| 6      | PTT_GND   |
| 7      | PTT+      |
| 8      | TX_AUDIO- |
| 9      | TX_AUDIO+ |


### RPi

| GPIO    | Pin | Function   |
| ------- | --- | ---------- |
| GPIO17  | 11  | PTT        |
| GPIO22  | 15  | SQL Det.   |
| GPIO18  | 12  | Fan Ctrl   |
| GPIO24  | 18  | Fan Tacho  |


### Jumper

| JP  | Function                |
| --- | ----------------------- |
| JP1 | Bypass PWM (always on)  |
| JP2 | Enable clipping diodes  |


## Usage

An example project which uses this board can be found at https://charly14.de/svxlink-installation-und-konfiguration/

## License
This repository is licensed under the CC-BY-SA. See the LICENSE file for details.

Concept ist based on the [SVXLink Interface by Aleksander, S65AL](http://lea.hamradio.si/~s57nan/ham_radio/svx_intf_rpi/svx_intf_rpi.html)
