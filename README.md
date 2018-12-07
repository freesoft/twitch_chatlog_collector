# Twitch Chatlog Collector
This is modified from Twitch Dev's ChatBot sample to collect some sample chat log from my Twitch TV channel. You can find the original repository [here](https://github.com/TwitchDev/chat-samples/tree/master/python).<br/>
Original implementation had some sample code about how to response for custom command( chat starts with !), especially for getting the Twitch channel's current playing game(e.g, Just Chatting, Overwatch, etc), changing the title, etc. However, I needed to collect the chat logs ONLY, not others, so you'll able to see some additional code that stores the chat logs in the file with same channel name. 

Although it's created and changed for my own chat channel, it can be used against any channel as long as your credentials(or oauth2 clientId) has permission to read a chat message in any given channel. <br/>
Make sure you are doing right, e.g, getting the permission from the channel owner or check any legal issue if there is any. Use it with your own risk and all the consequences are yours.



## Installation
After you have cloned this repository, use pip or easy_install to install the IRC library.

```sh
$ pip install irc
```

or you can simply installing it on Heroku. It doesn't have any web interface right now, so intalling it in the heroku won't do anything though. It requires web interface implementation so that app can take the channel name and run against it.
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)


## Usage
To run the chatbot, you will need to provide an OAuth access token with the chat_login scope.  You can reference an authentication sample to accomplish this, or simply use the [Twitch Chat OAuth Password Generator](http://twitchapps.com/tmi/).

```sh
$ python chatbot.py <username> <client id> <token> <channel>
```
* Username - The username of the chatbot. It will be either your twitch tv username, but can be any username that you created on twitch tv.
* Client ID - Your registered application's Client ID to allow API calls by the bot. If you don't have any registered Twitch App or client id, go [https://glass.twitch.tv/console/](https://glass.twitch.tv/console/) and create a new app. Then you'll be able to check your app's oauth2 client id. Copy it and use in here.
* Token - Your OAuth Token. It seems like it was password before, but it has replaced with oauth2 access token for security reason. IIRC token can includes user's credentials so it doesn't need username so I don't know why Twitch Dev makes the sample program this way, but it is what it is. If you get an oauth2 access token from above twitchapps.com/tmi/, the token value will have "oauth:" prefix. Use the token without "oauth:" prefix since this python code will add "oauth:" in front of given token string.
* Channel - The channel your bot will connect to. Check the exact channel name on Twitch.tv and use it as it is. It seems like the connection is case sensitive.


## Result

All the collected chat log will be stored in the file which has same names as the chat channel you deployed the bot. ( the one you specified in `<channel>` ). At the same time, the program will print out collected logs in the stdout.

I've run the program on my Mac OS High Sierra 10.13.6 with Python 3.6.5, and modified a few original lines to make this running on Python 3, so you might have to do so revert if you'd like to run it with Python 2.
