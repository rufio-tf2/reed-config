# Team Fortress 2 Scripts

## Table of Contents

- [Download files](#download-files)
- [Install](#install)
- [autoexec.cfg](#autoexeccfg)
  - [Alert Sniper](#alert-sniper)
  - [Alert Spy-On-Engi](#alert-spy-on-engi)
  - [Shift modifier](#shift-modifier)
  - [Silly](#silly)
- [reset.cfg](#resetcfg)
- [Spy](#spy)
  - [Custom shift modifier](#custom-shift-modifier-1)
- [Soldier](#soldier)
  - [Custom shift modifier](#custom-shift-modifier-2)

## Download Files

Most TF2 players aren't programmers, and don't have git, and that's fine.

You can download a zip of this repo [here](https://github.com/reeddunkle/cfg/archive/master.zip), or by clicking the green "Clone or download" button on the top right of this repo's [homepage](https://github.com/reeddunkle/cfg)

![Download ZIP](http://i.imgur.com/lF3GOYJ.png)

## Install

Once you've got this repo on your machine, place, copy, or move the `.cfg` files into your Steam's `cfg/` folder.

If you've chosen a custom location for your Steam folder, then you know where it is. If you used the default install path, then it may be:

* Windows: `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2\tf\cfg`
* macOS:

Restart TF2, and the `autoexec.cfg` will automatically run.

[🔝 Back to top](#table-of-contents)

## autoexec.cfg

### null

Create global `null` variable, set to an empty string

[🔝 Back to top](#table-of-contents)

### Silly

#### Need a dispenser here

Pressing HOME makes the SPACE button execute a jump and call for a dispenser. Pressing END resets the SPACE button to its default function.

## reset.cfg

### Utility

#### Added missing alerts

I added calls which alert your team of two vulnerabilities for which there are no built-in alerts (like there is for "Spy!").

##### Alert Sniper

[`alertSniper`](./autoexec.cfg#L9) - calls the "Incoming!" alert, and prints a message to your team saying that there's a sniper ahead.

##### Alert Spy-On-Engi

[`alertSpyOnEngi`](./autoexec.cfg#L9) - calls the "Incoming!" alert, and prints a message informing your team that a spy is actively sapping the engineer's buildings.

If a spy catches an engineer alone, it can be difficult for him to deal with him by himself while preserving all of his buildings. Often he has to choose between running the spy off, or removing his sappers.

#### Shift Modifier

After feedback on my [Reddit post](https://www.reddit.com/r/Tf2Scripts/comments/6eaer7/cfg_scripts_in_github_repo/), this now works differently.

The MOUSE buttons that I use with the shift-modifier are bound to variables `M1_key`, `M2_key`, and `M4_key`. The SHIFT button executes the `+shift_modifier` variable, which mutates the defition of the above variables.

When SHIFT is pressed, the `*_key` variables are assigned to the alerts. When SHIFT is released (`-shift_modifier`), they're assigned to my default buttons.

This is messy, but apparently nested binds can cause issues with other scripts, so it's the safer approach.

[🔝 Back to top](#table-of-contents)

## Soldier

### Rocket Jump

A standard rocket jumping script found everywhere online.

### Custom Shift Modifier

Identical to the shift-modifier in [reset](#resetcfg), but `M4_key` now has `+/-` states, bound to the `rocket_jump` script.

[🔝 Back to top](#table-of-contents)

## Pyro

I see people using a "Detonator Jump" script for use with the Pyro's [Detonator](https://wiki.teamfortress.com/wiki/Detonator). I'll probably set that up eventually.

[🔝 Back to top](#table-of-contents)

## Contributing

You can always fork and edit. If you notice better ways that I could be doing things, please open a PR.

## Set up your own cfg repo

My `.gitignore` file lists all the default files. Copy it into your `cfg/` directory. You can turn the directory into a git repo (run `git init`) and it will ignore the default files, and only add the custom files you set up.

In the future, I'll add more detailed instructions for those new to GitHub.

[🔝 Back to top](#table-of-contents)

## Thanks

Thanks to the community. This scripting takes getting used to, and I'm still figuring out the nuances. I couldn't have gotten into it if y'all weren't posting your scripts.

[🔝 Back to top](#table-of-contents)
