# WebServer - Webduino (Particle)

This is a port to work with the Particle TCPServer and TCPClient implementations. It is a lot faster then the [last port/implementation](https://github.com/m-mcgowan/Webduino), because that introduced the `fixmedelay()` macro of 20ms. A test request took 300ms with it and 30ms without... I assumed that the bug is solved (at least on the Photon it runs perfect). 

I actually hope this library gets obsolete soon, since there is already an HTTPServer implementation for Wiced (the [Particle Soft AP HTTP Server](https://docs.particle.io/reference/firmware/photon/#softap-http-pages) makes use of this). I hope that they open it up in the Particle API with AP support. Otherwise the [Adafruit HTTPServer implementation](https://learn.adafruit.com/introducing-the-adafruit-wiced-feather-wifi/adafruithttpserver) for their WICED Feather WiFi might be an interesting start (unfortunately I don't have the C skills to start with that). 

[Kasper Kamperman](https://www.kasperkamperman.com/)

# Webduino

This is an Arduino-based Web Server library, originally developed for a class at NYC Resistor. It's called Webduino, and it's an extensible web server library for the Arduino using the Wiznet-based Ethernet shields. It's released under the MIT license allowing all sorts of reuse.

## Features

- URL parameter parsing
- Handle the following HTTP Methods: GET, HEAD, POST, PUT, DELETE, PATCH
- Web Forms
- Images
- JSON/RESTful interface
- HTTP Basic Authentication

## Installation Notes

With Arduino 1.0, add the Webduino folder to the "libraries" folder of your sketchbook directory.

You can put the examples in your own sketchbook directory, or in hardware/libraries/webduino/examples, as you prefer.

If you get an error message when building the examples similar to "WebServer.h not found", it's a problem with where you put the Webduino folder. The server won't work if the header is directly in the libraries folder.

## Resources

- [Wedbuino Presentation on Google Docs](http://docs.google.com/present/view?id=dd8gqxt8_5c8w9qfg3)
- [A Wedbuino based file server](http://playground.arduino.cc//Main/WebduinoFileServer)


## Compatible Ethernet Shields

These have all been tested with the library successfully:

- [Freetronics Etherten](http://www.freetronics.com/products/etherten)
- [Freetronics Ethernet Shield](http://www.freetronics.com/products/ethernet-shield-with-poe)
- [Arduino Ethernet](http://arduino.cc/en/Main/ArduinoBoardEthernet)
- [Arduino Ethernet Shield, both original and updated microSD version](http://arduino.cc/en/Main/ArduinoEthernetShield)
- [Adafruit Ethernet Shield w/ Wiznet 811MJ module](http://www.ladyada.net/make/eshield/)
- [NKC Electronics Ethernet Shield DIY Kit](http://store.nkcelectronics.com/nkc-ethernet-shield-diy-kit-without-wiz812mj-mod812.html)

Shields using the Microchip ENC28J60 chip won't work with the library as that requires more software support for implementating
the TCP/IP stack.

## Version history

### 1.9.1 port to Particle in May 2017
- Uses new the [new Particle library](https://docs.particle.io/guide/tools-and-features/libraries/) structure. 

### 1.9 released in May 2016

- fixed bug with compatibility with original version of Ethernet library

### 1.8 released in Jan 2012

- added httpNotFound() method to output 404 error message
- added processConnection(uint8_t sock) and processConnection(uint8_t sock, char *buff, int *bufflen) methods
- increased size of 'm_contentLength' to 'long int'

### 1.7 released in Jan 2012

- fixed Google Code issue [4](http://code.google.com/p/webduino/issues/detail?id=4) where expect fails with high-ASCII characters due to sign issues
- fixed Google Code issue [8](http://code.google.com/p/webduino/issues/detail?id=8) by adding WEBDUINO_NO_IMPLEMENTATION macro that allows including the class definition without the implementation code
- fixed Google Code issue [9](http://code.google.com/p/webduino/issues/detail?id=9): allowing prog_char* strings for printP
- added httpServerError() method to output 500 Internal Server Error message
- added support for HTTP PUT, DELETE, and PATCH methods (see Google Code issue [11](http://code.google.com/p/webduino/issues/detail?id=11)
- fixed Google Code issue [12](http://code.google.com/p/webduino/issues/detail?id=12): off-by-one error in name/value parser (readPOSTparam) where the buffer wouldn't ever be completely filled
- updated copyright string for 2012 and major authors
- GitHub fork now the official version; all open issues on Google Code site fixed or closed and moved to GitHub

### 1.6 released in Jan 2012

- added [checkCredentials](http://ten-fingers-and-a-brain.com/arduino-projects/webduino/checkcredentials/) and [httpUnauthorized](http://ten-fingers-and-a-brain.com/arduino-projects/webduino/httpunauthorized/) methods as well as readHeader method for HTTP Basic Authentication; currently users will have to do the Base64 encoding outside of Webduino and I'm uncertain whether I ever want this inside the library or not...
- fixed the request parser: previously the command dispatcher would always pass true for tail_complete, even if the tail was incomplete
- fixed the command dispatcher: previously the default command could not have a tail, but the EPIC FAIL was returned

### 1.5 released in Dec 2011

- added a default favicon.ico based on the led.png from the Image example to save resources on Firefox trying to load this file on every request if it can't be loaded
- added keywords.txt for syntax highlighting in Arduino IDE
- bumped the version number up in response headers and compiler variables
- added version history to readme
- fixed default value for prefix
- fixed /index.html in Hello World example

### releases between Jul 2011 and Dec 2011

- project forked on GitHub by Chris Lee
- JSON/RESTful interface
- header Access-Control-Allow-Origin added
- code split in .h and .cpp files
- Arduino 1.0 changes by Dave Falkenburg and others
- adding CRLF after extraHeaders

### 1.4.1 released in Nov 2009

- fix examples to use readPOSTparam method

### 1.4 released in Sep 2009

- bug fix for multple connections

### 1.3.1 released in Aug 2009

- major bug fix for 1.3 for posts where Content-Length is last header sent

### 1.3 released in Aug 2009

- mostly robustness fixes (beta)

### 1.2.1 released in Aug 2009

- fixed HelloWorld example

### 1.2 released in Jul 2009

- now with GET parameter handling

### 1.1 released in Apr 2009

### 1.0 released in Mar 2009
