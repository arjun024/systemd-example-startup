# systemd-example-startup
example unit file to tell systemd to start a shell script at boot

## Configure

Place the unit service file in `/etc/systemd/system` (or your systemd unit file
search path if different) and the do the following:

	sudo systemctl enable example.service

In case your unit file is located located somewhere else, you may do the following:
(I do not recommed this)

	sudo systemctl link /path/to/example.service

Do note that here you have to give the full path and not just the unit file name.

To see a list of unit-files:

	sudo systemctl list-unit-files

You can then grep on this output for further info.

E.g. to list all enabled services:

	sudo systemctl list-unit-files | grep enabled


E.g. to view status of nginx service:

	sudo systemctl list-unit-files | grep nginx

## Take Note

* Make sure your shell script is executable. (`chmod +x`)
* Make sure your shell script begins with a sheband (`#!/bin/bash`)
