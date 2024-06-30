# Scripting_Remote_Commands

Script Pseudocode:

● Is named "run-everywhere.sh".

● Executes all arguments as a single command on every server listed in the
/vagrant/servers file by default.

● Executes the provided command as the user executing the script.

● Uses "ssh -o ConnectTimeout=2" to connect to a host. This way if a host is down, the script
doesn't hang for more than 2 seconds per down server.

● Allows the user to specify the following options:

-> -f FILE This allows the user to override the default file of /vagrant/servers. This way
they can create their own list of servers execute commands against that list.

-> -n This allows the user to perform a "dry run" where the commands will be displayed
instead of executed. Precede each command that would have been executed with
"DRY RUN: ".

-> -s Run the command with sudo (superuser) privileges on the remote servers.

-> -v Enable verbose mode, which displays the name of the server for which the
command is being executed on.

● Enforces that it be executed without superuser (root) privileges. If the user wants the remote
commands executed with superuser (root) privileges, they are to specify the -s option.

● Provides a usage statement much like you would find in a man page if the user does not
supply a command to run on the command line and returns an exit status of 1. All messages
associated with this event will be displayed on standard error.

● Informs the user if the command was not able to be executed successfully on a remote host.

● Exits with an exit status of 0 or the most recent non-zero exit status of the ssh command.
