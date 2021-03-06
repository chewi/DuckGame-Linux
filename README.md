# Duck Game Linux FNA patches
### Because Duck Game forgets to mkdir and wine is slow
##### MIT-licensed
----

[**Feel free to discuss this on Reddit!**](https://www.reddit.com/r/linux_gaming/comments/6zqrrx/duckgamelinux_fna_custom_steamworks_bindings_some/)  
[Screenshots](https://twitter.com/0x0ade/status/907745108010946560), [GamingOnLinux.com article](https://www.gamingonlinux.com/articles/want-to-play-duck-game-on-linux-well-its-possible-thanks-to-xnatofna.10339)  
0x0ade on [**Twitter**](https://www.twitter.com/0x0ade), [**Patreon**](https://www.patreon.com/0x0ade)


[**You can support me on Patreon!**](https://www.patreon.com/0x0ade)  
This project wouldn't be possible without the support from:
* Ethan Lee: Thank you for creating FNA!
* Artus Elias Meyer-Toms, Renaud Bedard and Ryan Kistner: I wouldn't be able to get my hands on the game without your support!

### Usage instructions:
**Preparations:**
* Get yourself a fresh copy of Duck Game, f.e. via Steam... through Wine... or from a friend with Windows.
* Install `mono-complete` and `libcurl3:i386` and `ffmpeg` (or matching) via your package manager.
    * `ffmpeg`, not "`libav`" / `avconv`.

**Installing / updating:**
* Download [**the latest released DuckGame-Linux-Complete.zip**](https://github.com/0x0ade/DuckGame-Linux/releases)
* Extract the .zip into the Duck Game directory. Overwrite the original files when extracting. `XnaToFna.exe`, and `DuckGame.exe` should be next to each other; The old `Steam.dll` should be replaced by the one in the .zip.
* Open terminal in Duck Game directory, run `chmod a+x ./mod.sh; ./mod.sh`
    * `mod.sh` creates a backup of important files in an `orig` subdirectory, which XnaToFna needs. It also gives all files in the directory read-write permissions for all users, otherwise both XnaToFna and MonoMod will fail.
* Run `mono DuckGame.exe` OR Launch the game via Steam (add `DuckGame.sh` to your library as "non-Steam game").
* Be a duck with a gun!

The game stores its save data in `~/DuckGame`, which is technically the same as on Windows.

### Current collection of patches:
* [XnaToFna](https://github.com/0x0ade/XnaToFna) gets the game running using [FNA](https://fna-xna.github.io/) instead of XNA. Thanks to [flibitijibibo](https://www.patreon.com/flibitijibibo) for FNA. Without him this wouldn't be possible!
* [Non-mixed-mode Steam.dll "proxy" to Steamworks.NET](https://github.com/0x0ade/DuckGame-Linux/tree/master/Steam) - this allows you to use Steam functionality natively... although it still contains a few holes. Working on it!
* More verbose fatal error logging that help you when patching the game.
* Create missing directories automatically. Does Windows just implicitly create the directories?!
* Automatically pass -nothreading because it's faster.
* Automatically pass -nomods because the mods would need to be relinked to FNA. This doesn't happen automagically yet.
* Fix `ModLoader.modHash == null`, not `"nomods"` when `-nomods` is passed. This also affects vanilla Duck Game and can kill Steam.

If for whatever reason something doesn't work, please create an issue on GitHub. I want this to work for everyone!
