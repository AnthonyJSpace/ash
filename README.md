# ash
A custom shell for Grey Hack the game, built using Viper 2.0 and OpenViper 3.0 as inspiration:
https://store.steampowered.com/app/605230/Grey_Hack/

This tool cannot be used for real world purposes and techniques demonstrated are not relevant to real 
world cyber security.

Ash is intended to be compiled and run as root on rental servers, though in single player games the 
home device is fine. Prior to the current release of the game, and potentially still present, some 
circumstances lead to the ip ash runs on being left in remote logs even if intermediate jumps are made 
before the target is breached. This makes launching on the home device a very bad idea for multiplayer 
game sessions.

As well as replacing the default bash prompt, ash includes tools to assist in reaching game objectives
including internal versions of some standard binary utilities. These are implemented as required to
both leverage the seperate tracking of working directory across different machines while infiltrating
networks and to provide essential commands if the current target shell does not have permissions to run
those commands locally. Any command not matching an internal command will fall back to searching /bin, 
/usr/bin and the current working directory.

The shell line header will appear like:
[192.192.19.22]:[192.168.1.22 (localhost)]——(root@pdp11 shell)

which should be read as

[ip_address]:[lan_ip_address]--(effective_user@computer_name access_type)

lan_ip address will have the postfix (localhost) when the user is on the machine ash was launched from

effective_user - ash guesses the access level on the target machine by checking read permissions. This 
resolves to root, user or guest permission levels.

access_type - whether a shell, computer or file object was returned by the exploit used.

(rkit) - is added to the information to indicate a rootkit (read jumpfile) is installed, allowing ash to operate 
on the target machine as if it was run from that machine, but using the home servers CPU for decryption speed.

