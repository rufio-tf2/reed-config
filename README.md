# Team Fortress 2 Config

## Table of Contents

- [What you get](#what-you-get)
  - [Additional actions](https://github.com/rufio-tf2/rufio-config/blob/master/cfg/actions.cfg)
  - [Improved settings](https://github.com/rufio-tf2/rufio-config/blob/master/cfg/settings.cfg)
  - [Shift-modifiers](#shift-modifiers-arrow_upper_right)
  - [Weapon-specific settings](#weapon-specific-settings-arrow_upper_right)
  - [Quick loadout switch](#quick-loadout-switch-arrow_upper_right)
  - [Quick class switch](#quick-class-switch-arrow_upper_right)
- [Download](#download-arrow_double_down)
- [Install](#install)
- [Uninstall](#uninstall)
- [Contributing](#contributing)

## What you get

This is not an [FPS config](https://github.com/mastercoms/mastercomfig). This config is a framework that provides missing features to TF2:

- [Additional actions](https://github.com/rufio-tf2/rufio-config/blob/master/cfg/actions.cfg) (e.g. `alertSniper`, `alertSpyOnEngi`)
- [Improved settings](https://github.com/rufio-tf2/rufio-config/blob/master/cfg/settings.cfg) (e.g. interp, fov, and crosshair)
- [Scripts](./cfg/scripts/README.md): _Shift-modifiers, Weapon settings, Quick loadout switch, Quick class switch_

You can swap in and out different parts of this config and customize the specifics.

### Shift-modifiers ([:arrow_upper_right:](https://github.com/rufio-tf2/key-modifiers))

These are some of shift actions that I use. For a more full explanation of how to work with these, [read this](https://github.com/rufio-tf2/key-modifiers).

- <kbd>SHIFT</kbd>+<kbd>MOUSE1</kbd> -- _Alert Spy_
- <kbd>SHIFT</kbd>+<kbd>MOUSE2</kbd> -- _Alert Sniper ahead_
- <kbd>SHIFT</kbd>+<kbd>MOUSE3</kbd> -- _Alert Spy is sapping engineer's buildings_
- <kbd>SHIFT</kbd>+<kbd>MWHEELUP</kbd> -- _Alert Incoming_
- <kbd>SHIFT</kbd>+<kbd>MWHEELDOWN</kbd> -- _Alert Incoming from behind_

#### Class-specific shift-modifiers

You can define all-class, and/or class-specific "shift-modified" versions of any key. But each key needs to be wired-up by doing a few things. I've got a handful of keys already wired-up that I use (the keys listed above, plus a [few more](./cfg/scripts/key_modifiers/keys)).

For example, these are different bindings that I tested my system against:

<details>
  <summary>Engineer</summary>
  <ul>
    <li>
      <kbd>MOUSE3</kbd> -- <em>Destroy sentry and build</em>
    </li>
    <li>
      <a href="https://github.com/rufio-tf2/rufio-config/blob/master/cfg/classes/engineer/key_modifiers">
        <code>classes/engineer/key_modifiers</code>
      </a>
    </li>
  </ul>
</details>

<details>
  <summary>Pyro</summary>
  <ul>
    <li>
      <kbd>MOUSE4</kbd> -- <em>Detonator jump</em>
    </li>
    <li>
      <a href="https://github.com/rufio-tf2/rufio-config/blob/master/cfg/classes/pyro/key_modifiers/">
        <code>classes/pyro/key_modifiers</code>
      </a>
    </li>
  </ul>

</details>

<details>
  <summary>Soldier</summary>
  <ul>
    <li>
      <kbd>MOUSE4</kbd>, <kbd>MWHEELUP</kbd>, <kbd>MWHEELDOWN</kbd> -- <em>Primary <--> Melee switchers</em>
    </li>
    <li>
      <a href="https://github.com/rufio-tf2/rufio-config/blob/master/cfg/classes/soldier/key_modifiers/">
        <code>classes/soldier/key_modifiers</code>
      </a>
    </li>
  </ul>
</details>

<details>
  <summary>Spy</summary>
  <ul>
    <li>
      <kbd>MOUSE4</kbd> -- <em>Last disguise</em>
    </li>
    <li>
      <a href="https://github.com/rufio-tf2/rufio-config/blob/master/cfg/classes/spy/key_modifiers/">
        <code>classes/spy/key_modifiers</code>
      </a>
    </li>
  </ul>
</details>

### Weapon-specific settings ([:arrow_upper_right:](https://github.com/rufio-tf2/rufio-config/blob/master/cfg/scripts/weapon_slot_settings.cfg))

This lets you load settings per weapon slot. For example, you could:

- Change the crosshair color for different slots like [Mr. Slin does](https://github.com/misterslin/CrosshairSwitcher)
- Use it to turn the viewmodel on/off for certain slots
- Etc.

#### Class-specific weapon-slot settings

In the previous example, I established base slot-settings for all of the classes. But you can also create class-specific slot overrides. I put those settings in a class's `key_modifiers.cfg` file.

### Quick loadout switch ([:arrow_upper_right:](https://github.com/rufio-tf2/quick-loadout-switch))

<details>
  <summary>Use the arrow keys to change your loadout.</summary>
  <ul>
    <li>:arrow_left: Loadout A</li>
    <li>:arrow_up: Loadout B</li>
    <li>:arrow_right: Loadout C</li>
    <li>:arrow_down: Loadout D</li>
  </ul>
</details>

I also have <kbd>ALT</kbd> bound to switch to Loadout A for quick resupply.

### Quick class switch ([:arrow_upper_right:](https://github.com/rufio-tf2/quick-class-switch))

<details>
  <summary>Use the numpad numbers to change your class.</summary>
  <ol>
    <li>Scout</li>
    <li>Soldier</li>
    <li>Pyro</li>
    <li>Demo</li>
    <li>Heavy</li>
    <li>Engineer</li>
    <li>Medic</li>
    <li>Sniper</li>
    <li>Spy</li>
  </ol>
</details>

## Download [[:arrow_double_down:](https://github.com/rufio-tf2/skeleton-config/archive/master.zip)]

If the link doesn't work, click the green "Clone or download" button on the top right of this page and click "Download ZIP".

<img src="https://i.imgur.com/OX9A0dt.png" width="50%" height="50%" alt="Download ZIP">

1.  Unzip my config to its own folder.
1.  Rename the config folder from `skeleton-config-master` to `skeleton-config`. (`master` is the [branch](https://guides.github.com/introduction/flow/))

## Install

#### Either, open your C:\Program Files (x86) and:

Navigate to your `tf` folder. If you've chosen a custom location for your Steam folder, then you know where it is. If you used the default install path, then it should be:

- Windows: `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2\tf\`
- macOS: `~/Library/Application Support/Steam/SteamApps/common/team fortress 2/tf/`
- Linux: `~/.steam/steam/SteamApps/common/Team Fortress 2/tf/`

#### Or, open Steam and:

1.  Right click TF2 in your Steam library
1.  Click Properties
1.  Go to the "Local Files" tab
1.  Click the "Browse Local Files..." button
1.  Open the `tf` folder

### 1. Back up your current settings

I recommend [making a backup](./docs/BACKUP.md) of your current settings in case you want to revert to your current setup. Also, remove any other configs you've got in place. You can even back up your whole `tf` folder if you want, it isn't that large.

I made a video showing you how to create a backup using the console:

- <https://youtu.be/XpQyBVroUrE>

### 2. Move config files

To install my files, open the `custom` folder that's inside of the `tf` folder. If `custom` doesn't exist, just create it.

1.  Navigate into `tf/custom/`
1.  Move `skeleton-config` into here

You should now have my config located at `tf/custom/skeleton-config`. Restart TF2 and everything should be setup.

**Note**: If anything is wonky after you install my config, please [let me know](https://github.com/rufio-tf2/skeleton-config/issues/new).

## Uninstall

Did you try out my config but want to revert to your backup? Read [this](./docs/UNINSTALL.md).

## Contributing

You can always fork and edit. If you notice better ways that I could be doing things, I welcome pull requests.

## Thanks

Thanks to the community. This scripting takes getting used to, and I'm still figuring out the nuances. I couldn't have gotten into it if you all weren't posting your scripts.

## Unlicense

This is free is all senses of the word. [UNLICENSE](./UNLICENSE)
