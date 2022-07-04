# UBC Solar Telemetry V2

## TLDR

**Car:** CANbus messages ⭢ STM transmit ⭢ radio module transmit

**Local Host:** Radio module receive ⭢ Python parse and transmit

**Web Server:** InfluxDB receive ⭢ Grafana display

## At a Glance

Messages from the CANbus of the car are received from an STM microcontroller.

The STM transmits the messages via UART to an XBEE radio module.

Outside of the car, on a raspberry pi, another radio module receives the UART stream.

The raspberry pi runs a python script to parse the UART stream found in the machine's serial port.

The python script writes the parsed data to an InfluxDB database.

A Grafana dashboard populates data by linking to the InlfuxDB database.

Other machines can view the local Grafana GUI and InfluxDB database by joining the same network as the raspberry pi.