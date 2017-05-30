# Team Fortress 2 Scripts

[autoexec](#autoexec)

## Install

Clone the repo: `git clone https://github.com/reeddunkle/cfg`

Place the `.cfg` files in the `cfg/` directory inside your `Steam/steamapps/common/Team Fortress 2/tf/cfg` folder:

If you've chosen a custom location for your Steam folder, then you know where it is. If you used the default install path, then it may be:

* Windows: `C:\Program Files (x86)\Steam\steamapps\common\Team Fortress 2\tf\cfg`
* macOS:
* Linux: *You can find it*

Restart TF2, and the `autoexec.cfg` will automatically run.

## autoexec.cfg

### null

Create `null` variable set to an empty string

### Utility

#### Added missing alerts

I added calls which alert your team of two vulnerabilities for which there are no built-in alerts (like there is for "Spy!").

##### [`alertSniper`](./autoexec.cfg#L9)

Calls the "Incoming!" alert, and prints a message to your team saying that there's a sniper ahead.


##### [`alertSpyOnEngi`](./autoexec.cfg#L9)

Calls the "Incoming!" alert, and prints a message informing your team that a spy is actively sapping the engineer's buildings.

If a spy catches an engineer alone, it can be difficult for him to deal with him by himself while preserving all of his buildings. Often he has to choose between running the spy off, or removing his sappers.

#### Shift-Alerts

Gets the base variables from [`get_shift_alert_base_variables.cfg`](./get_shift_alert_base_variables.cfg)

The variable [`+setBinds`](./autoexec.cfg#19) binds to my mouse buttons: the native "Spy!" alert (MOUSE1), `alertSniper` (MOUSE2), and `alertSpyOnEngi` (MOUSE4).
The variable [`-setBinds`](./autoexec.cfg#20) resets those MOUSE buttons to their default functions.

Finally, `+setBinds` is bound to the SHIFT button. Pressing shift calls `+setBinds`, releasing shift calls `-setBinds`, a hacky way to use SHIFT as a modifier key.

### Silly

Pressing HOME makes the SPACE button execute a jump and call for a dispenser. Pressing END resets the SPACE button to its default function.

## reset.cfg

This is called at the start of each class-specific cfg file to reset the keys I play with to their default behavior.

### null

I'm not positive if the variables defined in `autoexec.cfg` are made available to the other cfg files, so I make another `null` variable.

### ...rest

A lot of this is unnecessary and redundant. I'll probably pare this down in future commits. (For example, I never rebind, and never will rebind the 1, 2, or 3 buttons.)

The relevant resets, which I do fiddle with for specific classes, are the MOUSE buttons and the SPACE button.

## Spy

### Shift-Alerts

Gets the base variables from [`get_shift_alert_base_variables.cfg`](./get_shift_alert_base_variables.cfg), re-writes `bindM4-default` to `bind MOUSE4 lastdisguise`, re-declare `+setBinds` and `-setBinds` (using the new `bindM4-default`), and re-binds these to the SHIFT button.

**Note:** There's probably a better way to structure these files. Modularizing code in these scripts is inherently really messy. I'm open to ideas and suggestions.

## Soldier

### Rocket Jump

A standard rocket jumping script found everywhere online.

### Shift-Alerts

Like the [Spy](#spy), I declare a custom `bindM4-default` to use the Rocket Jump script, and re-declare

## Pyro

I see people using a "Detonator Jump" script for use with the Pyro's [Detonator](https://wiki.teamfortress.com/wiki/Detonator). I'll probably set that up eventually.

## Contributing

You can always fork and edit. If you notice better ways that I could be doing things, please open a PR.

## Thanks

Thanks to the community. This scripting takes getting used to, and I'm still figuring out the nuances. I couldn't have gotten into it if y'all weren't posting your scripts.
