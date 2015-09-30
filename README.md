# systemd-example-startup
example unit file to tell systemd to start a shell script at boot

## Configure

Place the unit service file in `\etc\systemd\system` (or your systemd unit file
search path if different) and the do the following:

	systemctl enable example.service

In case your unit file is located located somewhere else, you may do the following:
(I do not recommed this)

	systemctl link /path/to/example.service

and then

	systemctl enable /path/to/example.service

Do note that here you have to give the full path and not just the unit file name.
