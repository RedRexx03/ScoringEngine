Icons:
This directory contains Icons that a future version of install.py should set as the icons for the files being installed.

==========FILES ON THE CLIENT==========
install.py:
This file MUST be installed on the Linux image wanted to be scored. It downloads dependencies, downloads the scorebot from github(change the link in the file to the current version of the scorebot), and obfuscates it using "emojify"

scorebot.py:
The template scorebot, no vulnerabilities are scored here. It does not need to be installed on the Linux image since install.py will do that for you.


TeamInfo.py:
A GUi where you enter server settings. This is downloaded by install.py on the host to be scored. The syntax is-->
TeamName:Mode:ServerIP:ServerPort
If you are not using a server, just type in none:none:none:none. 

ScoringEngine.py:
This is not installed directly. install.py runs the emojify obfuscation methon on scorebot.py, deletes scorebot.py and replaces it with an obfuscated version called ScoringEngine.py so people can't just look inside for the answers. When the system reboots, the ScoringEngine script may stop. You can edit the install.py to add something into crontab with a message saying do not delete this. I just tell people to just re-run the scoring engine on startup.
==========FILES ON THE SERVER==========
Server.py:
ONLY put this on the server if you want one. A server is a separate Linux machine which the clients send their scores to(if configured). The scorebot.py will read the settings in TeamInfo.py to tell whether to send scores or not. If you are not using a Server, don't bother with configuring a server(TeamInfo.py is still needed).

ServerGrapher.py:
Takes the data that Server.py recieves from the clients and creates an html webpage featuring their graphs. You can project this on the board. The file already has methods to ensure that if people start the images at different times, the scores will still all start at the same time.