CleanerPlus - 10$
=================================================
Cleans map by timer or on spawning

* **Example** - *Delete junkpiles on respawn, delete campfires every 3600 seconds*

### Demostration:
```
No demonstration files
```

### Configuration:
```
{
  "Entities that will be cleared on spawn": [
    "bbq.deployed",
    "grenade.f1.deployed"
  ],
  "Clear Task List": [
    {
      "timer": 300.0,
      "entities": [
        "survey_charge.deployed"
      ]
    },
	{
      "timer": 3600.0,
      "entities": [
        "campfire"
      ]
    }
  ]
}
```

### Localization:
```
No language files
```