# Key Modifiers

Add modifier keys capabilities to TF2. You can't normally bind an action to <kbd>SHIFT</kbd>+<kbd>MOUSE1</kbd>, for example. This lets you use modifier keys like that. Use keys like <kbd>SHIFT</kbd> or <kbd>ALT</kbd> - or anything - to enable key combinations.

This framework organizes things by key. If you want to shift-modify a key, that key needs its own file. Then, that files needs to be wired in to this system.

There's a couple of things that need to be done for each key in order to wire it up so that it can be modified. Currently, these are the keys that are wired up, and already have their own file (the ones that I use):

- <kbd>ALT</kbd>
- <kbd>DOWNARROW</kbd>
- <kbd>LEFTARROW</kbd>
- <kbd>UPARROW</kbd>
- <kbd>RIGHTARROW</kbd>
- <kbd>KP_PLUS</kbd>
- <kbd>MOUSE1</kbd>
- <kbd>MOUSE2</kbd>
- <kbd>MOUSE3</kbd>
- <kbd>MOUSE4</kbd>
- <kbd>MWHEELDOWN</kbd>
- <kbd>MWHEELUP</kbd>

You can change use these and/or add new ones.

- [Changing a key](#changing-a-key)
- [Adding a new key](#adding-a-new-key)
- [Removing a key](#removing-a-key)
- [Creating class-specific states](#create-class-specific-states)

**Note**: This module depends on actions created in [`actions.cfg`](../../actions.cfg).

You can delete the MOUSE1.cfg file, but if you think you might want to use it in the future I'd just leave it sitting there.

## Changing a key

Let's pretend I want to change what <kbd>SHIFT</kbd>+<kbd>MOUSE2</kbd> does.

Right now it fires `alertSniper`, but let's say that instead I want it to let my teammates know that I popped uber.

There are three essential parts to each key's file. Here's the [`keys/MOUSE2.cfg`](./keys/MOUSE2.cfg) file:

```
//  Base
alias resetKey_MOUSE2 "alias +MOUSE2_key +CUSTOM_attack2; alias -MOUSE2_key -CUSTOM_attack2;"

//  Modifiers
alias shiftModifyKey_MOUSE2 "alias +MOUSE2_key alertSniper; alias -MOUSE2_key -CUSTOM_attack2;"

//  Set-up
resetKey_MOUSE2
bind MOUSE2 +MOUSE2_key
```

The `resetKey_MOUSE2` defines what MOUSE2 does when its unmodified, and `shiftModifyKey_MOUSE2` defines what it does when you press SHIFT, so that's what I'm going to change. The last part calls the reset command to initialize the base state, and then binds the key to its key-variable.

### 1. Set the modifier function to use the new action

I want to change

```
alias shiftModifyKey_MOUSE2 "alias +MOUSE2_key alertSniper; alias -MOUSE2_key -CUSTOM_attack2;"
```

to

```
alias shiftModifyKey_MOUSE2 "alias +MOUSE2_key alertUberPopped; alias -MOUSE2_key -CUSTOM_attack2;"
```

### 2. Create my new action

`alertUberPopped` doesn't exist yet, so I need to create it. I put all of my custom actions in [`actions.cfg`](../../actions.cfg).

```
//  actions.cfg
alias alertUberPopped "say_team Get excited, it's Uber time."
```

### A bug

There's reportedly an issue in TF2 scripting with using `bind` inside of an `alias`. I've tried it a few times, and I've had mixed results. To avoid it, I leave my shift modifier keys bound to an alias which has a `+/-` state. That's the `+MOUSE2_key` and `-MOUSE2_key` you see above in the shift modifier function.

When a key is bound to something without a `+/-` state, it just executes the thing that it's bound to. But when it's bound to something with a `+/-` state it fires the "`+`" action on keydown, and the "`-`" action on keyup. This is important for actions like `attack`, which continue until you let up the key.

When I modify a key to an action that doesn't have a `+/-` state, I put my action in place for the `+` state, and leave it wired up to its default (unmodified) `-` state.

### Alert and Use Uber

Imagine that I want <kbd>SHIFT</kbd>+<kbd>MOUSE2</kbd> to both notify my teammates _and_ pop the uber. I'll use the `alertUberPopped` from above, but I'll create a new action to accomplish this macro:

```
//  actions.cfg
alias alertUberPopped "say_team Get excited, it's Uber time."
alias +uberAndAlert "+attack2; alertUberPopped;"  // <-- This is what I want MOUSE2 to do
alias -uberAndAlert "-attack2;"
```

Next I put this action in the modifier function:

```
//  keys/MOUSE2.cfg
alias shiftModifyKey_MOUSE2 "alias +MOUSE2_key +uberAndAlert; alias -MOUSE2_key -uberAndAlert;"  // <-- Now your action does have both states
```

## Adding a new key

Here's an example of how to start modifying a new key that isn't currently in my list.

Let's say I want to wire up `F1`. I want its unmodified state to fake an uber call, and I want its shift-modified state to just call "Incoming!".

The point of a modifier is to give a key an additional state. Normally it performs a default action, but when I hold a "modifier key" it changes the key to perform a different action.

I'll need to define it's modified state -- what I want it to do while I'm holding Shift. Then, since it's a brand new file, I'll need to define its un-modified state -- what the key should do shift is **not** being pressed. Finally, I'll need to wire up both of these states.

### 1. Create new actions

I'd want to create a new action in [`actions.cfg`](../../actions.cfg). This isn't strictly necessary, but by defining this once in `actions.cfg`, I can now use `alertUberReady` to use the Uber Ready voice line. The name `alertUberReady` tells me what it does, as opposed to its console command `voicemenu 1 7` which tells me how, rather than what. "What" is more useful to read in most cases, and it's also usually easier to remember.

I stick this shortcut alias in my `actions.cfg` file, and use `alertUberReady` in the rest of the config to perform the action.

```
//  actions.cfg
alias alertUberReady "voicemenu 1 7;"
```

### 2. Create a new key file

In the [`keys`](./keys) folder, create a new file called `F1.cfg`. It's going to need three things:

- Reset function to return it to its unmodified state
- Shift-modify function to set it to its modified state
- Wired up

```
//  F1.cfg
//  Base
alias resetKey_F1 "alias F1_key alertUberReady;"

//  Modifiers
alias shiftModifyKey_F1 "alias F1_key alertSniper;"

//  Set-up
resetKey_F1
bind F1 F1_key
```

### 3. Include the new reset function in `resetKeys.cfg`

When this file executes, it fires all of the `resetKey` functions. It's critical that I add my new function to this list. I'll add it at the end of the list, but the order doesn't matter here.

```
//  resetKeys.cfg
resetKey_MOUSE1
resetKey_MOUSE2
resetKey_MOUSE3
resetKey_MOUSE4
resetKey_ALT
resetKey_MWHEELUP
resetKey_MWHEELDOWN
resetKey_F1  //  <-- Add this line
```

### 4. Include the new modifier function in `shiftModifiyKeys.cfg`

When this file executes, it fires all of the `shiftModify` functions. It's also critical that I add my new function to this list.

```
//  shift_modifiers/shiftModifyKeys.cfg
shiftModifyKey_MOUSE1
shiftModifyKey_MOUSE2
shiftModifyKey_MOUSE3
shiftModifyKey_MOUSE4
shiftModifyKey_ALT
shiftModifyKey_MWHEELUP
shiftModifyKey_MWHEELDOWN
shiftModifyKey_F1  //  <-- Add this line
```

## Create class-specific states

For example, on Spy I use MOUSE4 to use the `lastdisguise` action, but on Pyro I use it to perform `detonatorJump`. On both I keep the shift-modified version of MOUSE4 the same which is to `sayGameIsHard`.

In [`classes/pyro/key_modifiers.cfg`](../../classes/pyro/key_modifiers.cfg), first I create my new action. Then I create my new reset function. Finally I execute it the reset function, because I'm changing MOUSE4's _unmodified_ state. If I were changing its modified state, I wouldn't initalize the function like this, because the initial state should be its unmodified state.

```
//  pyro/key_modifiers.cfg
alias +detonatorJump "+jump; +duck; +CUSTOM_attack; +CUSTOM_attack2;"
alias -detonatorJump "-jump; -duck; -CUSTOM_attack; -CUSTOM_attack2;"

alias resetKey_MOUSE4 "alias +MOUSE4_key +detonatorJump; alias -MOUSE4_key -detonatorJump;"

//  Init
resetKey_MOUSE4
```

The Spy's [`key_modifier.cfg`](../../classes/spy/key_modifiers.cfg) is the same, except `lastdisguise` is a predefined action so I don't have to create it at the start.

## Create a new modifier key

Do you want to make ALT a modifier too? I put that in place a bit ago, but I ended up not liking it so I removed it. If you want ALT or some other key, [let me know](https://github.com/rufio-tf2/rufio-config/issues/new) and I'll help you out.

I'm still working on improving this system. If you have ideas or suggestions, on how to improve it [let me know](https://github.com/rufio-tf2/rufio-config/issues/new).

## Removing a key

Let's pretend that I no longer want to shift-modify MOUSE1. The simplest way is to go into [`keys/init.cfg`](./keys/init.cfg) and remove (or comment out) the MOUSE1 line:

```
exec scripts/key_modifiers/keys/MOUSE1  //  <-- Remove this line
exec scripts/key_modifiers/keys/MOUSE2
exec scripts/key_modifiers/keys/MOUSE3
```
