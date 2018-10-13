Loadout - 15$
=================================================
Allows players to set loadouts that will gived them on respawn. 
Group as default "default". Group with higher priority will be used as main loadout. 
Restrictions able to decreace amount of items on saving loadout. Set it to 0 to disable item spawning. They works only for group where they are. 

* **Permission to use** - *loadout.use*
* **Command** - */loadout*

### Demostration:
```
You can see video-demonstration [here]().
```

### Configuration:
```
{
  "Group settings": [
    {
      "permname": "default",
      "priority": 0,
      "restricted": {
        "rocket.launcher": 0,
        "ammo.pistol.hv": 128,
        "ammo.rifle": 128
      }
    },
    {
      "permname": "loadout.vip",
      "priority": 1,
      "restricted": {
        "rocket.launcher": 0
      }
    }
  ],
  "Wipe loadouts on change map?": false
}
```

### Localization:
```
{
  "SAVED": "Loadout was saved successfully!",
  "GIVED": "Loadout was gived successfully!",
  "USAGE": "/loadout <save/reset>",
  "RESET": "Loadout was cleared!",
  "CURRENT": "Your current loadout is:\n{0}",
  "LOADOUT": "Your can set your loadout by /loadout save!",
  "PERM": "Your dont have permission to use that command!"
}
```