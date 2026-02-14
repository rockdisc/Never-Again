#Tech #Personization 

# 0 Intro 
You are probably here because you messed up an update or something similar to that and all of my data is gone, lucky for you, I thought of this and am now making this. First things first, download the zip file and open it, it will have all of my pictures and everything. It should be in the backup ssd I have. 
Next go through all of the things below to get all of my ricing in, do this in the order they are written in case something were to go wrong, again. 

# 1 Deblout

```bash 
$ bash <(curl -fsSL https://raw.githubusercontent.com/DanielCoffey1/a-la-carchy/master/a-la-carchy.sh)
```
This is a la carte, a way of debloating Omarchy. Mainly we want to get rid of all web-apps aside from discord and most other packages installed here, honestly the only reason I am still using Omarchy is because copying all of this to arch is too much of a pain. 

# 2 Customizing 
After we have everything taken away that we do not need, lets customize the things we do need. 


## 2.1 Windows 
I know the Monitors were probably pissing you off, here is the fix: Put it in monitors 


Put this in Look and feel 
``` conf
# Change the default Omarchy look'n'feel

# https://wiki.hyprland.org/Configuring/Variables/#general
general {
    # No gaps between windows
    gaps_in = 3
    gaps_out = 3

    # Use master layout instead of dwindle
    # layout = master
}

windowrulev2 = opacity 0.7 0.6,class:^(obsidian)$

windowrulev2 = opacity 0.8 0.7,class:^(spotify)$



# https://wiki.hyprland.org/Configuring/Variables/#decoration
decoration {
    # Use round window corners
    # rounding = 8
}
```


## 2.2 Wallpapers & Theme 
In my pictures there is Sefirah Castle and Fragments of Me, those are your wallpapers unless we change them. Use Aether for the theme. 

## 2.3 Taskbar 

This is very customized, but this should work, maybe have to install a package for weather, but you can figure that out. 
``` json

  "reload_style_on_change": true,
  "layer": "top",
  "position": "top",
  "spacing": 0,
  "height": 26,
  "modules-left": ["custom/omarchy", "hyprland/workspaces"],
  "modules-center": ["mpris"],
  "modules-right": [ 
    "network",
    "custom/divide",
    "bluetooth",
    "group/audio",
    "custom/divide",
    "battery",
    "group/bright",
    "custom/divide",
    "custom/weather",
    "clock",
    "custom/divide",
    "custom/screenrecording-indicator"
  ],
  "hyprland/workspaces": {
    "on-click": "activate",
    "format": "{icon}",
    "format-icons": {
      "default": "",
      "1": "󰙎",
      "2": "",
      "3": "󰝚",
      "4": "4",
      "5": "5",
      "6": "6",
      "7": "7",
      "8": "8",
      "9": "9",
      "10": "0",
      "active": "󱓻"
    },
    "persistent-workspaces": {
      "1": [],
      "2": [],
      "3": [],
      "4": [],
      "5": []
    }
  },
  "custom/divide": {
    "format": "|"
  },
  "custom/omarchy": {
    "format": "∴",
    "on-click": "omarchy-menu",
    "on-click-right": "xdg-terminal-exec",
    "tooltip-format": "Omarchy Menu\n\nSuper + Alt + Space"
  },
  "custom/update": {
    "format": "",
    "exec": "omarchy-update-available",
    "on-click": "omarchy-launch-floating-terminal-with-presentation omarchy-update",
    "tooltip-format": "Omarchy update available",
    "signal": 7,
    "interval": 3600
  },
  "mpris": {
    "format": "▶ {title}",
    "format-paused": " ",
    "tooltip-format": "{artist} - {title}",
    "max-length": 50,
    "on-click": "playerctl play-pause",
    "on-click-right": "playerctl next",
    "on-click-middle": "playerctl previous"
  },
  "custom/weather": {
    "exec": "/usr/bin/waybar-weather -config /home/rockdisc/.config/waybar-weather/config.toml",
    "restart-interval": 60,
    "return-type": "json",
    "hide-empty-text": true,
    "on-click": "pkill -USR1 waybar-weather"
  },
  "clock": {
    "format": "{:%I:%M}",
    "tooltip-format": "{:%A %D}",
    "on-click-right": "omarchy-launch-floating-terminal-with-presentation omarchy-tz-select"
  },
  "network": {
    "format-icons": ["󰤯", "󰤟", "󰤢", "󰤥", "󰤨"],
    "format": "{icon}",
    "format-wifi": "{icon}",
    "format-ethernet": "󰀂",
    "format-disconnected": "󰤮",
    "tooltip-format-wifi": "{essid} ({frequency} GHz)\n⇣{bandwidthDownBytes}  ⇡{bandwidthUpBytes}",
    "tooltip-format-ethernet": "⇣{bandwidthDownBytes}  ⇡{bandwidthUpBytes}",
    "tooltip-format-disconnected": "Disconnected",
    "interval": 3,
    "spacing": 1,
    "on-click": "omarchy-launch-wifi"
  },
  "battery": {
    "format": "{icon}",
    "format-discharging": "{icon}",
    "format-charging": "{icon}",
    "format-plugged": "",
    "format-icons": {
      "charging": ["󰢜", "󰂆", "󰂇", "󰂈", "󰢝", "󰂉", "󰢞", "󰂊", "󰂋", "󰂅"],
      "default": ["󰁺", "󰁻", "󰁼", "󰁽", "󰁾", "󰁿", "󰂀", "󰂁", "󰂂", "󰁹"]
    },
    "format-full": "󰂅",
    "tooltip-format-discharging": "{power:>1.0f}W↓ {capacity}%",
    "tooltip-format-charging": "{power:>1.0f}W↑ {capacity}%",
    "interval": 5,
    "on-click": "omarchy-menu power",
    "states": {
      "warning": 20,
      "critical": 10
    }
  },
  "bluetooth": {
    "format": "",
    "format-disabled": "󰂲",
    "format-off": "󰂲",
    "format-connected": "󰂱",
    "format-no-controller": "",
    "tooltip-format": "Devices connected: {num_connections}",
    "on-click": "omarchy-launch-bluetooth"
  },
  "backlight/slider": {
    "min": 1,
    "max": 100,
    "orientation": "horizontal",
    "device": "intel_backlight"
  },
  "backlight": {
    "device": "intel_backlight",
    "format": "{icon}",
    "format-icons": ["", "󰃟", "󰃝", "󰃠"]
  },
  "pulseaudio": {
    "format": "{icon}",
    "on-click": "omarchy-launch-or-focus-tui wiremix",
    "on-click-right": "pamixer -t",
    "tooltip-format": "Playing at {volume}%",
    "scroll-step": 5,
    "format-muted": "",
    "format-icons": {
      "default": ["", "", ""]
    }
  },
  "pulseaudio/slider": {
    "min": 0,
    "max": 100,
    "orientation": "horizontal"
  },
  "group/audio": {
    "orientation": "inherit",
    "drawer": {
      "transition-duration": 600,
      "children-class": "tray-group-item"
    },
    "modules": ["pulseaudio", "pulseaudio/slider"]
  },
  "group/bright": {
    "orientation": "inherit",
    "drawer": {
      "transition-duration": 600,
      "children-class": "tray-group-item"
    },
    "modules": ["backlight", "backlight/slider"]
  },
  "group/tray-expander": {
    "orientation": "inherit",
    "drawer": {
      "transition-duration": 600,
      "children-class": "tray-group-item"
    },
    "modules": ["custom/expand-icon", "tray"]
  },
  "custom/expand-icon": {
    "format": " ",
    "tooltip": false
  },
  "custom/screenrecording-indicator": {
    "on-click": "omarchy-cmd-screenrecord",
    "exec": "$OMARCHY_PATH/default/waybar/indicators/screen-recording.sh",
    "signal": 8,
    "return-type": "json"
  },
  "tray": {
    "icon-size": 12,
    "spacing": 12
  }
}
```

And then for the [[CSS]] there is:
```css 
@define-color background #131211;
@define-color foreground #d2d4d2;


#pulseaudio-slider {
    padding: 0;
    margin-left:10px;
}
#pulseaudio-slider slider {
    min-height: 0px;
    min-width: 0px;
    opacity: 0;
    background-image: none;
    border: none;
    box-shadow: none;
}
#pulseaudio-slider trough {
    min-height: 2px;
    min-width: 80px;
    border-radius: 5px;
    background: black;
}
#pulseaudio-slider highlight {
    min-width: 3px;
    border-radius: 5px;
    background: white;
}

#backlight-slider slider {
    min-height: 0px;
    min-width: 0px;
    opacity: 0;
    background-image: none;
    border: none;
    box-shadow: none;
    background: none;
}
#backlight-slider trough {
    min-height: 2px;
    min-width: 80px;
    border-radius: 5px;
    background: black;
}
#backlight-slider highlight {
    min-width: 3px;
    border-radius: 5px;
    background: white;
}
```

## 2.4 Shortcuts and Inputs 

In Bindings have them as such: 
```hypr 
# Application bindings
$terminal = uwsm app -- $TERMINAL
$browser = omarchy-launch-browser

bindd = SUPER, RETURN, Terminal, exec, $terminal --dir="$(omarchy-cmd-terminal-cwd)"
bindd = SUPER SHIFT, F, File manager, exec, uwsm app -- nautilus --new-window
bindd = SUPER, B, Browser, exec, $browser
bindd = SUPER SHIFT, B, Browser (private), exec, $browser --private
bindd = SUPER, M, Music, exec, omarchy-launch-or-focus spotify
bindd = SUPER, N, Editor, exec, omarchy-launch-editor
bindd = SUPER SHIFT, T, Activity, exec, omarchy-launch-tui btop
bindd = SUPER SHIFT, D, Docker, exec, omarchy-launch-tui lazydocker

# If your web app url contains #, type it as ## to prevent hyperland treat it as comments

input {
    kb_options = caps:swapescape
}

# Overwrite existing bindings, like putting Omarchy Menu on Super + Space
# unbind = SUPER SHIFT, SPACE
# bindd = SUPER SHIFT, SPACE, Omarchy menu, exec, omarchy-menu
```

And in your inputs, have: 
```
# Control your input devices
# See https://wiki.hypr.land/Configuring/Variables/#input
input {
  # Use multiple keyboard layouts and switch between them with Left Alt + Right Alt
  # kb_layout = us,dk,eu
  kb_layout = us
  kb_options = compose:caps # ,grp:alts_toggle

  # Change speed of keyboard repeat
  repeat_rate = 40
  repeat_delay = 600

  # Start with numlock on by default
  numlock_by_default = true

  # Increase sensitity for mouse/trackpack (default: 0)
  sensitivity = 0.35

  touchpad {
    # Use natural (inverse) scrolling
  natural_scroll = true

    # Use two-finger clicks for right-click instead of lower-right corner
 clickfinger_behavior = true

    # Control the speed of your scrolling
    scroll_factor = 0.4
  }
}

# Scroll faster in the terminal
windowrule = scrolltouchpad 1.5, tag:terminal

# Enable touchpad gestures for changing workspaces
# See https://wiki.hyprland.org/Configuring/Gestures/
 gesture = 3, horizontal, workspace
```

# 3 Packages 

## 3.1 Mandatory & Utility 
Vivaldi 
Gimp 
Krita 
OpenTabletDriver 
Piper 


## 3.2 Fun 
PortProton 
Steam(ONLY AFTER PortProton)
Wine and TMNations Forever 


## 3.3 Rice Farm 
Cava 
Astroterm 
cbonsai 
discordo 
