# Ultimate Splinterlands Bot V1 (Modified version)
A fast, free, multi-account splinderlands bot

Based on https://github.com/PCJones/ultimate-splinterlands-bot

## Preamble 
Right now the code is a mess - I just hacked something together so I can release this asap. I'm planning on updating the code soon. 

Feel free to give suggestions for features/code refurbishing via github or on discord/telegram.


## New Features
- Multiple accounts with only one instance
- Login via Email
- Better Team Selection - the bot will chose cards with best win rate, not the ones that are most used
- Faster Login & Fighting:
- The bot no longer refreshes the page all the time (which often got you blocked from splinterlands for a few minutes)
- The bot clicks away popups
- The bot waits if there is a loading circle from splinterlands
- Disabled requesting the free API because it is always overloaded and slows down the bot (I've supplied a very large history file)
- Option to disable automatic quest reward chest opening
- Support for the private API of the original bot
- Minimum Energy Capture Rate - the bot will pause automatically if the energy capture rate is below a specified percentage
- New battle log summary after all battles
- New DEC log after battle. 
- Receive Battle log summary notification via Telegram 
- **Updated Feature**: Accurate battle summary 
- **Updated Feature**: Power Threshold and claimed reward log 
- **Updated Feature**: Auto gather the battle history for local back.(In case supported API is down)
- **Coming Soon**: Telegram notification if bot had an error/stop running. Call to function on telegram. (virgaux)
- Any suggestions?

# Support / Community

[Discord](
https://discord.gg/hwSr7KNGs9)

[Telegram](https://t.me/ultimatesplinterlandsbot) 

## How to install
- Download and install [NodeJs](https://nodejs.org/it/download/)
- Download the [bot](https://github.com/virgaux/ultimate-splinterlands-bot/archive/refs/heads/master.zip) (extract if its .zip)
- Create .env file (see .env-example)
- On windows: Execute `install.bat` in bot folder
- On MacOS/Linux: open terminal in bot folder and execute command `npm install` 

## How to start the bot
- On windows: Execute `start.bat` in bot folder
- On MacOS/Linux: open terminal in bot folder and execute command `npm start`

## Bot configuration:

Configuration with default values:

- `QUEST_PRIORITY=true` Disable/Enable quest priority

- `MINUTES_BATTLES_INTERVAL=30` Sleep time before the bot will fight with all accounts again. Subtract 2-3 minutes per account

- `ERC_THRESHOLD=80` If your energy capture rate goes below this the bot will stop fighting with this account until it's above again. Set to 0 to disable 
  
- `ERC_REGEN=true` Disable/Enable ERC regeneration function.

- `ERC_REGEN_LIMIT=100` If your energy capture rate is not yet above this, the bot will not fight with this account until it's reach the pre-set parameter.

- `CLAIM_SEASON_REWARD=false` Disable/Enable season reward claiming

- `CLAIM_QUEST_REWARD=true` Disable/Enable quest reward claiming

- `HEADLESS=true` Disable/Enable headless("invisible") browser (e.g. to see where the bot fails)

- `KEEP_BROWSER_OPEN=true` Disable/Enable keeping the browser instances open after fighting. Recommended to have it on true to avoid having each account to login for each fight. Disable if CPU/Ram usage is too high (check in task manager)

- `LOGIN_VIA_EMAIL=false` Disable/Enable login via e-mail adress. See below for further explanation

- `EMAIL=account1@email.com,account2@email.com,account3@email.com` Your login e-mails, each account seperated by comma. Ignore line if `LOGIN_VIA_EMAIL` is `false`

- `ACCUSERNAME=username1,username2,username3` Your login usernames, each account seperated by comma. **Even if you login via email you have to also set the usernames!**

- `PASSWORD=password1,password2,password3` Your login passwords/posting keys. Use password if you login via email, **use the posting key if you login via username**

- `USE_API=true` Enable/Disable the team selection API. If disabled the bot will play the most played cards from local newHistory.json file. **Experimental - set to false if you lose a lot**

- `API_URL=` Ignore/Don't change unless you have the private API from the original bot

- `USE_CLASSIC_BOT_PRIVATE_API=false` Set to false unless you have the private API from the original bot

- `TELEGRAM_NOTIF=false` Disable/Enable to receive telegram notification for battle result. 

- `TELEGRAM_TOKEN=` API TOKEN from telegram which will send you the notification. This is private key. DO NOT GIVE IT TO ANYONE. [how to get telegram token](https://www.siteguarding.com/en/how-to-get-telegram-bot-api-token)

- `TELEGRAM_CHATID` telegram chat id for notify, get the id: https://t.me/get_id_bot

# Donations

In case you want to donate to me for updating this bot, I would be very happy! Please also consider donating to the original bot creator.

- DEC into the game to the player **pcjones** or **virgaux**
- Bitcoin 3KU85k1HFTqCC4geQz3XUFk84R6uekuzD8
- Ethereum 0xcFE8c78F07e0190EBdD9077cF9d9E3A8DCED8d91 
- WAX to account **lshru.wam** (please copy the name)
- Text me on Discord or Telegram for anything other
- or 
- DEC into the game to the player **virgaux**
- Metamask wallet address: 0x6b11890566077AAC2B7fA7511d484f50Ec1335f6 
- Hive wallet address: @virgaux

# FAQ
**Can I have some accounts that login via email and some via username?**

Yes! Config Example:
```
LOGIN_VIA_EMAIL=true
EMAIL=account1@email.com,account2@email.com,username3
ACCUSERNAME=username1,username2,username3
PASSWORD=password1,password2,POST_KEY3
```

**How to get history data from users of my choice?**

1. Open battlesGetData.js in notepad and change the usersToGrab on line 70 to the users of your choice
2. Run `node battlesGetData.js` in the bot folder
3. File history.json is created, rename it to newHistory.json to replace the existing history data OR extend the newHistory.json file (see below)

**How to extend the newHistory.json without deleting existing data?**

1. Backup newHistory.json in case something goes wrong
2. Run `node combine.js` in the data folder to add the data from history.json to the newHistory.json file

**Why I can't see the Telegram notification after setting it up?**

1. Look for the name of your bot in Telegram. 
2. Type `/start` to receive notifcation once battle summary result is available. 
