Loot plus - 15$
=================================================
Plugin allows you to add/remove certain items in loot containers. Plugin works with every plugin that changing loot (LootPlus editing loot after them all)

* **Example** - *Add 'rifle.ak' with 'skin 12345' and 'chance 10%' to add to all containers*

### Demostration:
You can see video-demonstration [here](https://www.youtube.com/watch?v=TGwucodSffw).


### Configuration:
data file is used as configuration - 'oxide/data/LootPlus'

Additional - loot that will be added. **"all"** means that will happen to every crate that will be spawned.
```
{
  "all": [
    {
      "shortname": "rifle.ak",
      "skinID": 0,
      "amount": 1,
      "chance": 100
    }
  ],
  "crate_normal": [
    {
      "shortname": "rifle.ak",
      "skinID": 0,
      "amount": 1,
      "chance": 100
    },
    {
      "shortname": "pistol.semiauto",
      "skinID": 0,
      "amount": 1,
      "chance": 10
    }
  ]
}
```

```
{
  "all": [
    "scrap",
    "scarecrow"
  ],
  "crate_normal": [
    "techparts",
  ]
}
```

### Localization:
```
No language files
```
