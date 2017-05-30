# Team Fortress 2 Scripts

Contents:

[autoexec.cfg](#autoexeccfg)
- [Alert Sniper](#alert-sniper)
- [Alert Spy-On-Engi](#alert-spy-on-engi)
- [Shift modifier](#shift-modifier)
- [Silly](#silly)

[reset.cfg](#resetcfg)

[Spy](#spy)
- [Custom shift modifier](#custom-shift-modifier-1)

[Soldier](#soldier)
- [Custom shift modifier](#custom-shift-modifier-2)

## Install

Clone the repo:]

```
git clone https://github.com/reeddunkle/cfg
```

Place the `.cfg` files in the `cfg/` directory inside your `Steam/steamapps/common/Team Fortress 2/tf/cfg` folder:

If you've chosen a custom location for your Steam folder, then you know where it is. If you used the default install path, then it may be:

* Windows: `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2\tf\cfg`
* macOS:

Restart TF2, and the `autoexec.cfg` will automatically run.

[🔝 Back to top](#team-fortress-2-scripts)

## autoexec.cfg

[Link](./autoexec.cfg) to file

### null

Create `null` variable set to an empty string

### Utility

#### Added missing alerts

I added calls which alert your team of two vulnerabilities for which there are no built-in alerts (like there is for "Spy!").

##### Alert Sniper

[`alertSniper`](./autoexec.cfg#L9) - calls the "Incoming!" alert, and prints a message to your team saying that there's a sniper ahead.


##### Alert Spy-On-Engi

[`alertSpyOnEngi`](./autoexec.cfg#L9) - alls the "Incoming!" alert, and prints a message informing your team that a spy is actively sapping the engineer's buildings.

If a spy catches an engineer alone, it can be difficult for him to deal with him by himself while preserving all of his buildings. Often he has to choose between running the spy off, or removing his sappers.

#### Shift Modifier

Gets the base variables from [`get_shift_alert_base_variables.cfg`](./get_shift_alert_base_variables.cfg)

The variable [`+setBinds`](./autoexec.cfg#19) binds to my mouse buttons: the native "Spy!" alert (MOUSE1), `alertSniper` (MOUSE2), and `alertSpyOnEngi` (MOUSE4).
The variable [`-setBinds`](./autoexec.cfg#20) resets those MOUSE buttons to their default functions.

Finally, `+setBinds` is bound to the SHIFT button. Pressing shift calls `+setBinds`, releasing shift calls `-setBinds`, a hacky way to use SHIFT as a modifier key.

[🔝 Back to top](#team-fortress-2-scripts)

### Silly

#### Need a dispenser here

Pressing HOME makes the SPACE button execute a jump and call for a dispenser. Pressing END resets the SPACE button to its default function.

## reset.cfg

[Link](./reset.cfg) to file

This is called at the start of each class-specific cfg file to reset the keys I play with to their default behavior.

A lot of this is unnecessary and redundant. I'll probably pare this down in future commits. (For example, I never rebind, and never will rebind the 1, 2, or 3 buttons.)

The relevant resets, which I do fiddle with for specific classes, are the MOUSE buttons and the SPACE button.

[🔝 Back to top](#team-fortress-2-scripts)

## Spy

[Link](./spy.cfg) to file

### Custom Shift Modifier

Gets the base variables from [`get_shift_alert_base_variables.cfg`](./get_shift_alert_base_variables.cfg), re-writes `bindM4-default` to `bind MOUSE4 lastdisguise`, re-declare `+setBinds` and `-setBinds` (using the new `bindM4-default`), and re-binds these to the SHIFT button.

**Note:** There's probably a better way to structure these files. Modularizing code in these scripts is inherently really messy. I'm open to ideas and suggestions.

[🔝 Back to top](#team-fortress-2-scripts)

## Soldier

[Link](./soldier.cfg) to file

### Rocket Jump

A standard rocket jumping script found everywhere online.

### Custom Shift Modifier

Like the [Spy](#spy), I declare a custom `bindM4-default` to use the Rocket Jump script, and re-declare `+setBinds` and `-setBinds`, and bind them to SHIFT.

[🔝 Back to top](#team-fortress-2-scripts)

## Pyro

[Link](./pyro.cfg) to file

I see people using a "Detonator Jump" script for use with the Pyro's [Detonator](https://wiki.teamfortress.com/wiki/Detonator). I'll probably set that up eventually.

[🔝 Back to top](#team-fortress-2-scripts)

## Contributing

You can always fork and edit. If you notice better ways that I could be doing things, please open a PR.

[🔝 Back to top](#team-fortress-2-scripts)

## Thanks

Thanks to the community. This scripting takes getting used to, and I'm still figuring out the nuances. I couldn't have gotten into it if y'all weren't posting your scripts.

[🔝 Back to top](#team-fortress-2-scripts)
