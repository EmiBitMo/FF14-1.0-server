
# Installing Manually
## Requirements
  - Install and start desired web server
  - Install and start desired PHP processor
  - Install and start desired SQL engine
## Database
- Create a database named ffxiv_server
- Confirm that the sql server is set with the following behavioral defaults:
sql-mode="NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
- Load the SQL files of <Project Meteor Server source code location>\data\sql\ into the database
## Login Server
- Copy the following to web server: <Project Meteor Server source location>\data\www
  - OPTIONAL: If you have modified the database login settings, change them at:
<web server www folder>\config.php
- Restart the web server service
- Navigate to http://<web server ip>/create_user.php and create a new account

## Compiling Lobby and Game Server
- Navigate to the location the game client has been installed to and copy the following file:

  >FINAL FANTASY XIV client install location>\client\script\rq9q1797qvs.san

- Navigate to the location of the server source code and rename rq9q1797qvs.san to:

  >Project Meteor Server source location>\data\staticactors.bin
  
  - OPTIONAL: You can configure the IP address, port, database name, and database password for both the lobby server and map server under:
  
  >Project Meteor Server source location>\data\
  
- Compile the server 
Note: If you had compiled it before this, use Rebuild Solution instead of Build Solution to confirm that all the data files are copied properly
Setting up Lobby, World and Map Servers

  -OPTIONAL: If the server and client are on different machines, edit the server IPs in the following locations <Project Meteor Server source location>\data\(lobby/map/world)_config.ini <SQL database>\ffxiv_server\servers <SQL database>\ffxiv_server\server_zones *if the map servers are not on the same server as world server
  
- Copy lobby_config.ini from <Project Meteor Server source location>/data/
to <Project Meteor Server source location>\Lobby Server\bin\(Debug\Release)\

- Copy map_config.ini, staticactors.bin and the scripts folder from <Project Meteor Server source location>/data/
to <Project Meteor Server source location>\Map Server\bin\(Debug\Release)\

- Copy world_config.ini from <Project Meteor Server source location>/data/
to <Project Meteor Server source location>\World Server\bin\(Debug\Release)\

## Starting the servers
1. Confirm all WAMP/web services are running
2. Run the lobby server: <Project Meteor Server source location>\Lobby Server\bin\(Debug\Release)\Lobby Server.exe
3. Run the map server: <Project Meteor Server source location>\Map Server\bin\(Debug\Release)\Map Server.exe
4. Run the map server: <Project Meteor Server source location>\World Server\bin\(Debug\Release)\World Server.exe

Setting up with a WAMP stack application can streamline this process. For this instruction, WAMP64 is reccomended.

# Setting up with WAMP
## Installing WAMP
  1. Download and install WAMP
  2. Start the server by clicking on the WampServer64 icon created by the installer
  3. Verify all services are properly started by checking on the W Icon in the notification bar:
   - Green: All services started properly
   - Yellow: Some services started properly
   - Red: All services have stopped
Note: Start/restart/stop the WAMP server by clicking on the W icon and selecting Start/Stop/Restart All Services


## Setting Up the Database
1. Confirm all WAMP services are installed
2. Left Click the WAMP status icon
3. Open MySQL → my.ini
4. Find the line containing
sql-mode="STRICT_ALL_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_ZERO_DATE,NO_ZERO_IN_DATE,NO_AUTO_CREATE_USER"
and change it to
sql-mode="NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
5. Restart the MySQL service (if not already started) by left clicking the WAMP status icon and selecting MySQL → Service Administration → Restart Service
6. Download, install, and run HeidiSQL
7. Select the New button to create a new connection and select Open
Note: If the SQL server IP/username/password differ from the defaults, change them here, otherwise continue to the next step
8. Verify you are connected:
A newly set up/blank mysql server should have the following databases listed:
Default tables
information_schema	mysql	performance_schema	sys
9. Right Click Unnamed and go to Create new → Database and name the new database: ffxiv_server
Note: If you changed the name of the server in step 3, the name will be that instead of Unnamed
10. Click the new ffxiv_server database entry
11. Go to File → Run SQL File and navigate to the <Project Meteor Server source code location>\data\sql\ folder
12. Select all SQL files in the folder, and execute them.
Note: HeidiSQL may warn you about mixed linebreaks, or an empty warning prompt after executing the query. Ignore them, it'll still run the query successfully.
## Setting Up the Login Server
1. Confirm all WAMP services are running
2. Navigate to the location of the server source code
3. Copy all of the data/www/login_su folder contents from the source code folder to the WAMP install location
The default location is: C:\wamp64\www
4. OPTIONAL: If you have modified the database login settings, change them at:
<web server www folder>\config.php
5. Restart the WAMP services
## Compiling Lobby and Game Server
1. Navigate to the location the game client has been installed to and copy the following file:
<FINAL FANTASY XIV client install location>\client\script\rq9q1797qvs.san
2. Navigate to the location of the server source code and rename rq9q1797qvs.san to:
<Project Meteor Server source location>\data\staticactors.bin
3. OPTIONAL: If the server and client are on different machines, edit the server IPs in the following locations:
<Project Meteor Server source location>\data\config.ini
<SQL database>\ffxiv_server\servers
4. Compile the server (See #Compiling)
Note: If you had compiled it before this, use Rebuild Solution instead of Build Solution to confirm that all the data files are copied properly
Setting up Lobby, World and Map Servers
OPTIONAL: If the server and client are on different machines, edit the server IPs in the following locations <Project Meteor Server source location>\data\(lobby/map/world)_config.ini <SQL database>\ffxiv_server\servers <SQL database>\ffxiv_server\server_zones *if the map servers are not on the same server as world server

- Copy lobby_config.ini from <Project Meteor Server source location>/data/
to <Project Meteor Server source location>\Lobby Server\bin\(Debug\Release)\
-  Copy map_config.ini, staticactors.bin and the scripts folder from <Project Meteor Server source location>/data/
to <Project Meteor Server source location>\Map Server\bin\(Debug\Release)\
- Copy world_config.ini from <Project Meteor Server source location>/data/
to <Project Meteor Server source location>\World Server\bin\(Debug\Release)\
