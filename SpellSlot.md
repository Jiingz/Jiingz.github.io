# SpellSlot

```cpp
name
missile_name
[summoner_spell_type](SummonerSpellType%20b8e61f5b3d9042c9b8fbe5f77fac447b.md)
level
ready_at
time_charge
```

## Usage

Those are supposed to be treated as Function. This means:

```cpp
game:GetPlayer().Q.name

-- unit is supposed to be treated as a local variable in a function holding a GameObject
unit.Q.name
```