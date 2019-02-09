# systemd-example-startup
example unit file to tell systemd to start a shell script at boot


# Scenario

You want to turn on an nginx or node.js server or run any arbitrary piece of code on system startup. What do you do? You write a shell script `/path/to/startup.sh` that does it all and configures systemd to run this script for you on every boot. 


## Configure

Edit the given unit service file (`example.service`) to your requirement. Change the value of `ExecStart` to your startup shell script, `PIDFile` to the pid file of whatever you're interested in, `ExecStop` and `ExecReload` to how you want to stop and reload it etc.

Place the unit service file (`example.service`) in `/etc/systemd/system` (or your systemd unit file
search path if different) and the do the following:

	sudo systemctl enable example.service

In case your unit file is located located somewhere else, you may do the following:
(I do not recommed this)

	sudo systemctl link /path/to/example.service

Note that here you have to give the full path and not just the unit file name.

To see a list of unit-files:

	sudo systemctl list-unit-files

You can then grep on this output for further info.

E.g. to list all enabled services:

	sudo systemctl list-unit-files | grep enabled


E.g. to view status of nginx service:

	sudo systemctl list-unit-files | grep nginx



* Make sure your shell script is executable. (`chmod +x`)
* Make sure your shell script begins with a shebang (`#!/bin/bash`)
