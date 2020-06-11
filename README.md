# Disptch-Discord-Game-Store - Commands Tutorial
This is a resumed tutorial for Dispatch your game to Discord Store - Only commands

# Configure Dispatch
1- WIN KEY + PAUSE BREAK
<br>
<img height="200" src="https://www3.bellmts.ca/file_source/mts.ca/Support/Support_Files/Images/windowssettings.jpg"/>
<br>
2- Go to Var system
<br>
<img height="700" src="https://i.imgur.com/SkVdq3H.png"/>
<br>
3- Click in "Patch" and click in "Edit" click in "New" and add C:\DiscordGames<br>
4- Download Dispatch in Discord Developers - Documentation and put Dispatch.exe inside folder created above.<br>
5- Create a file "Config.json"<br>
6 - Paste and change this inside your config file.<br>
```
{
  "application": {
    "id": <application_id>,
    "manifests": [{
      "label": "MY-GAME-NAME/windows",
      "platforms": ["win32", "win64"],
      "locales": ["pt-BR"],
      "local_root": ".",
	  "redistributables": [
		"directx_june_2010",
		"vcredist_2013_x64",
		"vcredist_2013_x86",
		"vcredist_2012_update_4_x64",
		"vcredist_2012_update_4_x86"
	  ],
      "launch_options": [{
        "name": "MY-GAME-NAME",
        "executable": "Launcher.exe",
        "arguments": [],
        "platforms": ["win32", "win64"],
        "working_dir": "."
      }]
    }]
  }
}
```

7- Below is all the comamnd list for usage.

```
# Using Dispatch commands - Discord Sell Game Store

# Authenticate
dispatch login

# Create Branch (Alpha, Beta, Final)
dispatch branch create <application_id> master

# List branch's
dispatch branch list <application_id>

# Protect game logon, discord need open to start the game
dispatch build drm-wrap <application_id> GameFolder\Game.exe

# Upload Game content files to discord storage
dispatch build push <branch_id> "config.json" GameFolder

# Publish (Synchronize to discord store/library)
dispatch build publish (application_id) <branch_id> <build_id>

# Delete a Branch by id (Alpha, Beta, Final)
dispatch branch delete <application_id> <branch_id>

# Delete a Build
dispatch build delete <application_id> <build_id>

# Branch promote (Promotes the live build of one branch to another)
dispatch branch promote <application_id> <branch_id_1> <target_branch_id_2>
# branch_id_1			=> Is the actual branch
# target_branch_id_2	=> Transfer branch branch_id_1 to target_branch_id_2

# Update build
dispatch build update <application_id> <branch_id> C:\my-game --platform win64 --locale pt-BR
```
