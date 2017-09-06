# Discord.js Music Plugin

This module way be buggy and need some fine tuning. Feel free to let me know what problems you encounter by opening an issue on the repo.
This was originaly an update of the original by [ruiqimao](https://github.com/ruiqimao/discord.js-music), but is now a updated version by [nexu-dev](https://www.npmjs.com/package/discord.js-music-v11) for [Discord.js](https://discord.js.org/)'s version 11.2^. Fixes deprecated warnings, video playback issues, along with various other add-ons and tweaks.

__The commands available are:__  
* `help [command]`: Displays help text for commands by this addon, or help for a specific command.
* `play <url>|<search string>`: Play a video/music. It can take a URL from various services (YouTube, Vimeo, YouKu, etc). You can also search using a string.
* `skip [number]`: Skip a song or multi songs with skip [some number],
* `queue`: Display the current queue.
* `pause`: Pause music playback. (requires music manager).
* `resume`: Resume music playback. (requires music manager).
* `volume`: Adjust the playback volume between 1 and 200 (requires music manager).
* `leave`: Clears the song queue and leaves the channel.
* `clearqueue`: Clears the song queue.

__Permissions:__  
* If `anyoneCanSkip` is false then only admins and the user that requested the song can skip it.
* Only admins can change volume or resume/pause music. (changing this to work like skipping in the future)

__Things I added & Changed:__  
* Videos won't (or are otherwise less likely to) end before the song stops.
* Help command added.
* Text replies were changed.

__Pre-installation:__  
1. `npm install discord.js` // The core discord.js framework (recommended stable > dev branch).  
2. `npm install ffmpeg-binaries` or `ffmpeg installed` // Allows the bot to join voice (yes its required).  
3. `npm install node-opus` or `npm install opusscript` // Required to stream audio. Discord prefers node-opus, but it is your choice.

__Installation:__  
1. `npm install discord.js-musicbot-addon`

__Common installation issues:__  
__Issue:__ FFMPEG was not found on your system, so audio cannot be played. Please make sure FFMPEG is installed and in your PATH.  
__Fix:__ `npm install ffmpeg-binaries`  
__Issue:__ Couldn't find an Opus engine.  
__Fix:__ `npm install node-opus` or `npm install opusscript`  
__Issue:__ Any node-gyp errors. (build fail, missing cl.exe, etc.)  
__Fix:__ This one is a little more complicated.  
1. Download and install [Visual Studio 2015](https://www.visualstudio.com/downloads/)  
2. New project -> Visual C++  
3. Install Visual C++  

If that doesn't fix your issue;  
1. Download and install the [Windows 8.1 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-8-1-sdk)

This is a music plugin for Discord.js. Using it is as easy as:  
```javascript
const Discord = require('discord.js');
const music = require('discord.js-musicbot-addon');
const <client> = new Discord.Client(); //replace <client> with what you want your Discord Client to be. Don't include < > on your client.

<client>.on('ready', () => {
    console.log(`[Start] ${new Date()}`);
});

music(<client>);
<client>.login(token);
```

The module consists of a single function, which takes two arguments:  
```javascript
/*
 * @param {Client} client - The discord.js client.
 * @param {object} options - (Optional) Options to configure the music bot. Acceptable options are:
 * 		prefix: The prefix to use for the commands (default '!').
 * 		global: Whether to use a global queue instead of a server-specific queue (default false).
 * 		maxQueueSize: The maximum queue size (default 20).
 * 		anyoneCanSkip: Allow anybody to skip the song.
 * 		clearInvoker: Clear the command message.
 * 		volume: The default volume of the player (1 to 200, default 50).
 */
music(<client>, options);
```