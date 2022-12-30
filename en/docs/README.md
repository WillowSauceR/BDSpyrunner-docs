﻿# BDSpyrunnerW Docs

Welcome to the `BDSpyrunnerW Docs`!
This document will help you develop plugins for BDSpyrunnerW.

## Requirements

1. have read the README and have successfully installed pyr.
2. Knowledge of Python3, go to [Official Website](https://www.python.org/about/gettingstarted/) to learn it.
3. have a good heart for research.

## Start

If you have met the above requirements, you can start writing the plugin

### 1. Create a new file

Create myplugin.py in the plugins/py directory and type the following:

```py
import mc

help(mc)
```

After saving, start BDS and you will see the details of the mc module

### 2. Listening to in-game events

BDSpyrunner uses Detours to hook the BDS function points to intercept and listen for events.
We can use the setListener function to bind a function to an event, as follows.

```py
import mc

def onUseItem(e):
	print(e)
mc.setListener('onUseItem',onUseItem)
```

Save and start BDS, go to the server and
When you use the item, some relevant data will be printed on the console.

### 3. Get entity data

With all this data coming back from the listener, what do we do with it?
Take a look at the following example

```py
import mc

def onUseItem(e):
	player = e['player']
	pos = player.pos
	msg = f"{p.name} used item at {pos}"
	print(msg)
	player.sendTextPacket(msg)
mc.setListener('onUseItem', onUseItem)
```

Save the file in ``UTF-8`` format to support Chinese
Start BDS, enter the game and use the item, you will see the output in the console
Actually `player` is an object of Entity class, `name` and `pos` are its properties.
`sendTextPacket` is its member function.

## Extensions

In addition to the above example, we provide a rich set of other interfaces.

* [API](/docs/API.md)
* [Listener](/docs/Listener.md)

## End

Well now that you have fully mastered the basics of plugin development
Go ahead and get creative!