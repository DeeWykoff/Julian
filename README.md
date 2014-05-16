Julian
======

Mount samba shares from a server




1	Open Nemo as root.
2	Make a root folder named whatever you call the server.
3	Copy all the files in here into that folder.
4	Make Start and Unmount executable

5	This script needs to run as root at startup

 If you have an rc.local type situation then put this in it
 /Folder/Start &
 The ampersand makes it asnychronous

 If you have systemd then you need to run it as a service
 Go to /etc/systemd/system
 Make a file called Servername.service
 It should look like
   [Unit]
   Description=Mount shares from server

   [Service]
   ExecStart=/Servername/Start

   [Install]
   WantedBy=multi-user.target

 Run this command
 systemctl reenable Servername

 To stop it from running
 systemctl disable Servername
