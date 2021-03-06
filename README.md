# Twitch Chatr Bot

The intention of this bot is to provide a way to merge twitch chats while a streamer is co-streaming; we want to 'import' the co-streamer's chat into our chat.

## MVP

- [X] Specify/identify co-streamer and merge chat from their stream into our streamer's chat
- [X] ~Use the same visual that twitch uses for chat merge if possible~
    * If not possible then identify the user in some manner that it's coming from co-stream
- [X] Able to configure bot for each co-streamer
    * Able to specify at least one co-stream but more if possible
        * An upper limit of four-six should be fine
- [X] Easy to run bot
    * Assuming we will probably need the bot to be run locally because the configuration will need to change per co-stream
    * Assuming hosting will be hard because of configuration changes at least until full website available and multi-tenant

## VP

- [X] Able to configure bot to ignore some chat messages
    * Specify users
    * Specify commands (maybe start with anything that starts with !)
- [X] Have random actions the bot can take
    * This should be configurable, action(s) and time
- [ ] ~If possible then the co-streamer's mod control our chat too (i.e. delete messages)~
    * ~Can we confirm this is what twitch does too?~
- [X] Allow chat merging from discord too
    * Configurable channel used for chat merging
    * ~Configurable highlighting of chat merging~

# Configuration

```
"BotConfig": {
    "name": "Chatr",
    "token": "oauth:ChatrToken",
    "channel": "streamer"
    "destinations": [
      "destination1"
    ],
    "sources": [
      "source1"
    ],
    "ignoreChatFrom": [
      "ignore1"
    ],
    "ignoreCommandFrom": [
      "ignore1"
    ],
    "timers": [
        {
            "interval": 0,
            "minInterval": 0,
            "maxInterval": 0,
            "commands": [
                "command1"
            ],
            "type": "<BasicTimer, RandomTimer>"
        }
    ]
},

"DiscordBotConfig": {
    "token": "token",
    "channel": "channel",
    "enabled": false,
},
```

1. Name - The bot's name (might not really do anything)
2. Token - OAuth token
3. Channel - This streamer's channel
4. Destinations - Additional channels to echo chat
5. Sources - Co-streamer's that we want to merge chat from
6. IgnoreChatFrom - A list of user's that we should ignore any chat messages
7. IgnoreCommandFrom - A list of user's that we should ignore any commands

# Notes

* Can use https://twitchapps.com/tmi/ to create an oauth token
* Seems we must use TCP vs WebSockets, should confirm
* We are setup to only respond to commands from the streamer's channel
* 500 max message size
