# How to set up your Physgun database for use with servers running the impulse framework

Author: hondacivic, Owner @ react: Half-Life 2: Roleplay

This guide will explain how to configure your database to be used with any schema that uses the impulse framework. Due to how the framework was written originally, there will be errors with the creation of characters and RP groups, as certain fields do not have a default value. Since Physgun databases have strict mode enabled, you will need to follow this guide in order to use Physgun MySQL databases with your impulse framework server.

## Requirements + Prerequisites

Before starting this guide, you must have installed a MySQL client. This guide will use DBeaver, to set it up you can follow this guide:
https://help.physgun.com/en/article/how-to-inspect-modify-your-physgun-game-server-database-data-18wlmk0/

You should also have defined your database details in your config.yml. If you haven't done so, go to your game panel, go to Management, then Databases, and note your database details.
![image](https://github.com/user-attachments/assets/3a73bccf-41c2-4eba-8773-72cc50c0e44a)

Then go to File Manager, go to garrysmod/data, create a folder named "impulse", and then inside that folder, create a file named "config.yml".
![image](https://github.com/user-attachments/assets/ca9a1446-d8c2-49f7-930f-980b59ab2b70)

Inside config.yml, input your database details like so:
```
db:
  ip: "ip - connection in the database tab, without the port number"
  username: "username in the database tab"
  password: "password in the database tab"
  database: "name in the database tab"
  port: 3306
```

Then, save config.yml.


* List Optional
* Requirements Here
* Using the asterisk as a list

### Step Process

Short summary of what the reader will be doing in these steps below.

1. Step 1
2. Step 2
3. Step 3
... and so on, these are just general guidelines please feel free to be creative and add more below if you think it will help the reader!
