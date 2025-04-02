# How to set up your Physgun database for use with the impulse framework

Author: hondacivic___, Owner @ react: Half-Life 2: Roleplay

This guide will explain how to configure your database to be used with any schema that uses the impulse framework. Due to how the framework was written originally, there will be errors with the creation of characters and RP groups, as certain fields do not have a default value. Since Physgun databases have strict mode enabled, you will need to follow this guide in order to use Physgun MySQL databases with your impulse framework server.



## This guide is strictly for servers that use the impulse framework! It will not work for other gamemodes.

## Requirements + Prerequisites

Before starting this guide, you must have installed a MySQL client. This guide will use DBeaver, to set it up you can follow this guide:
https://help.physgun.com/en/article/how-to-inspect-modify-your-physgun-game-server-database-data-18wlmk0/

You also should have already installed impulse onto your server. Follow the installing impulse guide that should have come with the documentation in order to install the framework and schema on your server.

To use impulse, you need MySQLOO installed, which can be installed following this guide:
https://help.physgun.com/en/article/how-to-install-mysqloo-for-your-garrys-mod-server-drvt9q/

You also need Falco's Prop Protection - get it from
https://github.com/FPtje/Falcos-Prop-protection
and put in your garrysmod/addons folder.

You should also have defined your database details in your config.yml. If you haven't done so, go to your game panel, go to Management, then Databases, and note your database details.
![image](https://github.com/user-attachments/assets/3a73bccf-41c2-4eba-8773-72cc50c0e44a)

Then go to File Manager, go to garrysmod/data, create a folder named "impulse", and then inside that folder, create a file named "config.yml".
![image](https://github.com/user-attachments/assets/ca9a1446-d8c2-49f7-930f-980b59ab2b70)
(You can ignore the other folders in the screenshot- they will be created when you run the gamemode for the first time and are not relevant to this guide.)

Inside config.yml, define your database details:
```
db:
  ip: "ip - connection in the database tab, without the port number"
  username: "username in the database tab"
  password: "password in the database tab"
  database: "name in the database tab"
  port: 3306
```

Then, save config.yml.

Set your gamemode to the name of your schema, and then run your server.
Once you see
``` [mysql] Connected to the database! ```
in your server console, you can proceed with the rest of the guide.

> [!NOTE]  
> If you're getting the error ```[impulse] [SERIOUS FAULT] DB connection failure... Attempting reconnection...``` in your console, verify that you input your database details into config.yml correctly, and that config.yml is in the proper location (garrysmod/data/impulse/config.yml), and then restart your server.

**Once impulse is able to connect to the database, shut down your server before proceeding.**

### Editing the impulse database

When impulse is ran for the first time on a server, it will run a script that creates the database. However, it was designed for databases that have strict mode off- Physgun databases have strict mode enabled. The issue lies with certain fields that don't have default values and will cause errors whenever a player creates their character, so we will edit the database to allow for null values in these fields.

1. Open DBeaver and connect to your database. Refresh if you were connected prior to running impulse for the first time.

2. In the left navigation bar, expand Databases, then your database name, then Tables, and select "impulse_players".

![image](https://github.com/user-attachments/assets/d92978ad-59e6-48aa-ab50-6638ecd9a45d)

3. Select the Properties tab, and then uncheck "Not Null" next to the fields "rpgroup" and "rpgrouprank", which should look like the screenshot below. Press "Save" at the bottom of the screen to save your changes.

![image](https://github.com/user-attachments/assets/3f3dbfe6-181a-4dcc-8403-5bc49ecb14b7)

4. Go to "impulse_rpgroups" in the left navigation bar, and then select the Properties tab again. This time, uncheck "Not Null" for the field "type". Press "Save" at the bottom of the screen to save your changes. 

![image](https://github.com/user-attachments/assets/ee0c48f3-2c0d-40ae-8674-1d26295e1c07)

5. Start your server again. Join your server, and then create your character- you should be able to create a character without any MySQL callback errors in your console. You should also be able to create an F6 RP group without any errors.

> [!NOTE]
> If you haven't already, give yourself superadmin through the server console by doing ```impulse_setgroup "STEAM_X:X:XXX" superadmin```, where "STEAM_X:X:XXX" is your own SteamID. Don't forget to include the quotation marks!
