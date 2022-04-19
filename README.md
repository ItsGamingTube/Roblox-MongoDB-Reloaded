# Roblox MongoDB Reloaded

Roblox MongoDB Reloaded is a plugin for Roblox that allows you to interact with your MongoDB databases easily!

All features:
- Up to 200% faster than other MongoDB plugins
- Easy to setup
- Password protection
- Low resource usage (RAM, CPU, Disk)
- Similar to Datastore v2
- Repl.it and Heroku compatible
- No data loss on leave
- Multiple connections support
- Multiple server locations support
- Free to use
- Customizable API
- Free support included

## Frontend Installation

The Frontend is used to host the API connector on a Node.JS server.
To get started, download the latest Roblox MongoDB Reloaded version from our website or from our github page and install the required packages using the package manager, [npm](https://www.npmjs.com/).
```bash
npm install
```

### Configuration

To configure the Frontend, you must have env installed.

Here is a template that you can use for your Frontend configuration:
```json
{
  "MONGO_PASS": "your database password",
  "MONGO_USER": "your database user",
  "PASSWORD": "auth password",
  "USERNAME": "auth user"
}
```

After the first step is done, change the database url in the server.js file at line 12.

```java
mongoose.connect(`mongodb+srv://${mongoUser}:${mongoPass}@cluster0.ljtru.mongodb.net/gameDatabase?retryWrites=true&w=majority`, {useNewUrlParser: true, useUnifiedTopology: true });
```
If using MongoDB Atlas, just change the server url after ${mongoPass}@ and the database name.
If using an external database, replace the whole connection url with the suitable connection url.

Finally, if required, change the port in the main file (server.js) at the line 44.

## Backend Installation

The Backend that is hosted on Roblox is used to send POST requests and GET requests on the Frontend server.
To get started, download the latest Backend version from our website or from the github releases tab and open up your Roblox studio game.

**IMPORTANT NOTICE: Your place MUST be published and it MUST HAVE HTTP REQUESTS ON in the game settings!!!** If turned off, the Backend will fail to work. Also please note that if you want to test your database system, you must publish the game (private or public) and play on the Roblox Client.

After downloaing the Backend files, put the main module into ServerScriptService and modify the Backend configuration (in the Configuration Folder).

## Usage

```lua
local Db01 = require(script.Parent.MongoDBService)
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
Rmc:GetStore("StoreName", playerInstance)
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


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.
