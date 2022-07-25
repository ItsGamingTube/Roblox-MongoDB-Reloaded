# Roblox MongoDB Reloaded

A NodeJS app for Roblox that allows you to interact with your MongoDB databases easily!

### Features:
- Up to 200x better than most plugins.
- Beginner Friendly.
- Password Protection: Keep your database safe.
- Extremely low resource consumption (RAM, CPU, Disk).
- Similar to Datastore v2.
- Repl.it, Heroku, Glitch and Shared Hosting compatible.
- No Data Loss on leave.
- Multiple connections support.
- Multiple server locations support.
- Free to use forever.
- Customizable API.
- Free support included.

## Frontend Installation

The Frontend is used to host the API on a NodeJS server, so later we can send POST and GET requests on the server. You will need a NodeJS hosting such as Repl.it (Free), Heroku (Free), Glitch (Free), or any other compatible hosting before continuing.

To get started, download the latest Roblox MongoDB Reloaded version from our website or from the Github page, unzip the file (using 7ZIP), upload the unziped files on the server and install the required packages using the package manager, [npm](https://www.npmjs.com/).
```bash
npm install
```

### Configuration

Before configuring the Frontend, you must have env installed on your hosting. If you don't have it pre-installed, install it using the npm package manager (see tutorials on Youtube).

Here is a template that you can use for your Frontend configuration:
```json
{
  "MONGO_PASS": "MongoDB Datababse password",
  "MONGO_USER": "MongoDB Datababse user",
  "MONGO_URL": "MongoDB Database URL",
  "MONGO_DB_Name": "MongoDB Database Name",
  "PASSWORD": "Authentication password",
  "USERNAME": "Authentication user"
  "PORT": "Authentication user"
}
```

MONGO_PASS = (Example: mysecretpassworddatabase) Your database's password, instructions can be found on the software's website or on your hosting provider website. 

MONGO_USER = (Example: adminuser) Your database's user, instructions can be found on the software's website or on your hosting provider website. 

MONGO_URL = (Example: cluster0.i3et1.gcp.mongodb.net) Your database's URL used to connect, instructions can be found on the software's website or on your hosting provider website. 

MONGO_DB_Name = (Example: coinsdb01) Your database's Name. 

PASSWORD = (Example: mysecretapipassword) Password used for Authentication. 

USERNAME = (Example: rootuserapi) Username used for Authentication. 

PORT = (Default: 3000) Changes on which port the app runs. Only change if you know what you are doing.

## Backend Installation

The Backend that is hosted on Roblox is used to send POST requests and GET requests on the Frontend server.
To get started, download the latest Backend version from our website or from the github releases tab and open up your Roblox studio game.

**IMPORTANT NOTICE: Your place MUST be published and it MUST HAVE HTTP REQUESTS ON in the game settings!!!** If turned off, the Backend will fail to work. Also please note that if you want to test your database system, you must publish the game (private or public) and play on the Roblox Client.

After downloaing the Backend files, put the main module into ServerScriptService and modify the Backend configuration (in the Configuration Folder).

## Usage

```lua
local MongoReloaded = require(script.Parent.MongoDBService)
local players = game.Players

players.PlayerAdded:Connect(function(plr)
	local coinStore = Db01:GetStore("Coins", plr)
	print(coinStore:Get(50))
	
	wait(5)
	
	coinStore:Set(100)
	print(coinStore:Get(50))	
end)
```

### Methods:
```bash
MongoReloaded:GetStore("StoreName", playerInstance)
```
Creates or gets an existing store, for using the :Get and :Set methods.

```bash
Store:Get(DefaultValue)
```
This method accepts a default value to be used if there isn’t data for the player previously.

```bash
Store:Set(Value)
```
This method accepts the value to update in the store.

You don’t need to do anything for saving actually, everything is done internally in module .

### AntiExploit
We made this project with security in mind. That's why the module is stored in ServerScriptService. However, exploiters can still find ways to exploit it. We update the plugin regulary, but you can also make your own anti exploit for additional protection.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.
