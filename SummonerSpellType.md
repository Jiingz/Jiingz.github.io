# SummonerSpellType

```cpp
enum class SummonerSpellType {
  NONE,
  GHOST,
  HEAL,
  BARRIER,
  EXHAUST,
  CLARITY,
  SNOWBALL,
  FLASH,
  TELEPORT,
  CLEANSE,
  IGNITE,
  SMITE,
  RECALL,
  WARD
};
```

## Usage

Those are supposed to be treated as Function. This means:

```cpp
SummonerSpellType:None()
SummonerSpellType:Ghost()
SummonerSpellType:Heal()
...
```