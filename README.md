# Twitch GIF Commander

Display a GIF Or MP4 (or any image / video) in a browser (to be captured with OBS), which change regarding Twitch chat messages content.

Fork from project developped for @[Omnisnash](https://github.com/omnisnash/twitch-gif-commander), feel free to reuse.

![preview](https://imgur.com/a/UQNQe9y)

## Installation

````
npm install
````

## Configuration

- Place your GIFs/MP4/Content in the `./public/content` folder
- Be sure to have a `default.png`, which will be displayed by default

- A image is played for Config.resetAfter MS (default 5 secondes) then go back to default.png
- A video is played only once time then go back to default.png

- A content can be display once every Config.timeBetweenMsg (default 10 secondes)

Then, create a `config.json` file at the project root level with the following content:

````json
{
    "twitch": {
        "botUsername": "Twitch-GIF-Commander",
        "oauthToken": "<your_token>",
        "channelName": "roxxorrr_du_91"
    },
    "contents": [
        {
            "triggerOn": ["cute", "phoque", "seal"],    
            "file": "cutieseal.mp4",                    
            "type": "video/mp4"                         
        },
        {
            "triggerOn": ["clap", "bravo", "gg", "👏" , "👏👏", "👏👏👏", "👏👏👏👏" , "👏👏👏👏👏"],
            "file": "happy-clap-clapping.gif",
            "type": "image"
        },
        {
            "triggerOn": ["quoi", "?", "kua"],
            "file": "mister-v-tu-veux-quoi-toi.gif",
            "type": "image"
        },
        {
            "triggerOn": ["salaud", "salau", "salo"],
            "file": "usul-salaud.gif",
            "type": "image"
        },
        {
            "triggerOn": ["pamoi", "pasmoi", "caché", "cacher"],
            "file": "hide.gif   ",
            "type": "image"
        }
    ],
    "defaultContent" :
        {
            "triggerOn": [], 
            "file": "default.png",  
            "type": "image" 
        },
    "resetAfter": 5000,     
    "timeBetweenMsg": 10000 
}
````

**Twitch configuration**

- `botUsername` name of the bot
- `oauthToken` authentication token from https://twitchapps.com/tmi/
- `channelName` channel chat to watch

**Content configuration**

- `triggerOn` keywords which trigger the GIF change
- `file` the filename to display, WITH the extension
- `type` the type : "image" for png / gif ... "video/mp4" for mp4 "video/webm" for webm

**defaultContent**

- "triggerOn" : not used, do not touch
- "file" : name of file, if you want to update it you need to update index.html too
- "type" : not used, do not touch

**Other configuration**

- `resetAfter` (in ms) time before reverting the displayed Image to `default.png` (Video are read once and then come back)
- `timeBetweenMsg` (in ms) time before taking a new request
  
## Run

````
npm start
````

Start a web server on http://localhost:4242 with gif
