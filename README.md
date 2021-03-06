# zwave.js

A comprehensive stack for managing a home Z-Wave network, written in node.js JavaScript,  based loosely on the [Open Z-Wave project](http://code.google.com/p/open-zwave/).

## Project goals

* A low-level driver to interact with a USB dongle Z-Wave controller.  Systems based on the Zensys serial API should work with this sytem.  I am developing with the [Z-Stick Series 2](http://www.aeon-labs.com/site/products/view/2/).

* A service frontend for interaction with web clients, to be based on the Express node.js
module.

* A client interface with a highly-dynamic, non-modal interaction with the service
front-end.

## Status

### What works

* The entire init sequence completes successfully for the driver.

* Available nodes are queried.

* Basic node details are collected.

### What is next

* Lots of low-level work:
    * Naturally, actually allow for control and feedback of individual node settings, starting with simple light controllers.
    * Persistently cache data related to the node network so it doesn't all necessarily need to be determined at every launch.
    
### What will eventually be really cool

* "Plugin" support to allow custom programming.  E.g., create a plugin that will turn
on a group of lights if your computer's screen saver is deactivated, cycle a light if you get email, bring up lights gradually at dusk, etc.

* A scalable interface that will work well from any web browser, especially mobile devices.

### What is not in scope

* HID-based USB dongles.  I'm not working on anything currently that doesn't use the
virtual serial port interfaces.  In truth, I'm only working on the Aeon Labs Z-Stick 2 controller.

* Everything.  I'm definitely going to start with an eye toward implementing the Z-Wave controllers that I actually have, and work out from there _if time_.

* A focus on platforms beside Mac OS X.  Theoretically, using vanilla node.js, 
portable node.js modules, and web browsers for UI, this system will work on other OSs, but I'm not spending any effort on that right now.

## Setup

The first thing you want to do in a freshly-cloned repo is execute the following in a shell:

    make npm

That's it.  Ideally, that will just work and grab the modules that zwave.js requires.

## Application Usage

Currently, the system only provides one working integration test sample.  This is invoked as a normal node.js command:

    node test/zwtestapp.js
    
For help, run:

    node test/zwtestapp.js --help

Which will print something like this:

	Reading config from /Users/payton/.zwave.js
	zwtestapp.js command line options:
	  values are set with the following precedence:
	    command line options > 
	    config options (from ~/.zwave.js) > 
	    built-in defaults 
	<option> : <currently configured value>
	  --dev : /dev/cu.SLAB_USBtoUART

Which means there is one option, ```--dev```, which defaults to ```/dev/cu.SLAB_USBtoUART```.  For reference, this is the virtual serial port driver that the system will use to interact with the USB Z-Wave controller.

## Library Usage

Details on how to use the library in your own application will be described sometime in the future.  In the meantime, the application samples will illustrate common library usage details.

## License

(c) Payton R White 2012

This project cribs a bit from Open Z-Wave, so it will use the same license, the **LGPL v3**,
except where other components are used that have established licenses.

