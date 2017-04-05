keep-trying
===========

The `keep-trying` command executes a given command every X minutes, and stops after Y minutes, or when the command succeeds. It's useful for trying to run a command that, for example, uses input data that may or may not be available yet.

This script assumes the command passes or fails based on the exit status of the command, so if you're running your own script as the command, make sure it exits with the proper exit status (0 for success, anything else for failure).

Installing
----------

Clone the repo:

    $ git clone https://github.com/mikecharles/keep-trying.git

Install:

    $ make install

This will install the `keep-trying` script in `~/bin` (it will create the `~/bin` directory if it doesn't already exist).

Examples
--------

Run `~/bin/myscript.sh` every 5 minutes for an hour

    $ keep-trying -s 5 -t 60 ~/bin/myscript.sh

Run `~/bin/myscript.sh` every 5 minutes for an hour, including command line options, and email `email.address@gmail.com` if there was an error:

    $ keep-trying -s 5 -t 60 -e email.address@gmail.com ~/bin/myscript.sh opt1 opt2

Run `~/bin/myscript.sh` every 5 minutes for an hour, including command line options, redirect all output to a log file, and email `email.address@gmail.com` the log file if there was an error:

    $ keep-trying -s 5 -t 60 -e email.address@gmail.com -l ~/myscript.log ~/bin/myscript.sh opt1 opt2

Run `~/bin/myscript.sh` every 5 minutes for an hour and email `email.address@gmail.com` a message about the failure, including a custom email subject:

    $ keep-trying -s 5 -t 60 -e email.address@gmail.com -s "Something bad happened..." ~/bin/myscript.sh
