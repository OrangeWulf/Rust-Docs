Loadout - 15$
=================================================
Allows players to set loadouts that will gived them on respawn. 
Group with higher priority will be used as main loadout. 
Restrictions works only for group where they are. Group as default "default"

* Permission to use - **loadout.use**
* Command - /loadout

### Demostration:
You can see video-demonstration [here]().

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