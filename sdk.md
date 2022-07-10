# League8 - SDK Documentation

**CTRL + SHIFT + L FOR DARK MODE!**

## Callbacks

```lua
--Triggered right before OnUpdate
function OnPreUpdate(core) end

--Triggered right before OnUpdate.Main Logic should be called here!
function OnUpdate(core) end

--Triggered after OnUpdate. All visuals of your Plugin should be handled here.
function OnDraw(core, ui) end

--Triggered once a Unit recieves a buff.
function OnBuffGain(core, unit, buff) end

--Triggered once a Unit recalls.
function OnRecall(core, unit) end

--Triggered once a Unit teleports. Including special cases like Shen R.
function OnTeleport(core, unit) end

--Triggered once a Unit sets a new Path/does a new movement command.
function OnNewPath(core, waypoint, unit) end

--Triggered once a Missile has been created (not all Spells are Missiles!!)
function OnMissile(core, missile) end

--Config loading should be handled here.
function LoadCfg(config) end

--Config saving should be handled here.
function SaveCfg(config) end
```

## Usage

The paramter ‘core’ is your main connection to the core. You can check all it’s Functions at the ‘Core’ part of this Documentation.

## Core Functions

## Properties

```lua
-- all those are std::vectors containing the corresponding GameObject.
champs
minions
jungle
turrets
missiles
others
------
time
is_chat_open
```

## Functions

```cpp
int GetTickCount()
GameObject GetHoveredObject()
GameObject GetPlayer()
[MapObject](League8 - SDK Documentation 1a9de27ae2a14c4eb053c21a53e109e9/MapObject%207a9dabe8c967467e92625fda3dc4a6bf.md) GetMap() -- Returns a [MapObject](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/MapObject%207a9dabe8c967467e92625fda3dc4a6bf.md) of the current Map you are playing on.
GetObjectByIndex(int index)
GetObjectByNetId(int networkID)
GetBestTarget(UnitTag type, float range)
IsScreenPointOnScreen(Vector2 point)
IsWorldPointOnScreen(Vector3 point)
WorldToScreen(Vector3 point)
WorldToMinimap(Vector3 point)
Distance(GameObject unit1, GameObject unit2)

-- Drawing functions
DrawLine(Vector2 start, Vector2 end, float thickness, Color color)

-- points represents the amount of line points. 100 represents a clean circle.
DrawCircle(Vector2 center, float radius, int points, float thickness, Color c)

-- points represents the amount of line points. 100 represents a clean circle.
DrawCircleFilled(Vector2 center, float radius, int points, float thickness, Color c)

-- points represents the amount of line points. 100 represents a clean circle.
DrawCircleWorld(Vector3 center, float radius, int points, float thickness, Color c)

-- points represents the amount of line points. 100 represents a clean circle.
DrawCircleWorldFilled(Vec3 center, float radius, int points, Color c)
DrawText(Vector2 pos, string text, Color c)
DrawRect(Vector4 box, Color color, float rounding, float thickness)
DrawRectFilled(Vector4 box, Color color, float rounding, float thickness)
DrawRectWorld(Vector3 p1,Vector3 p2,Vector3 p3,Vector3 p4,float thickness,Color c)
DrawTriangleWorld(Vector3 p1, Vector3 p2, Vector3 p3,float thickness,Color c)
DrawTriangleWorldFilled(Vector3 p1, Vector3 p2, Vector3 p3, Color c)
DrawButton(Vector2 pos, string text, Color cButton, Color cText, float rounding)
DrawImage(string imageName, Vector2 start, Vector2 end)
DrawImageRounded(string imageName, Vector2 start, Vector2 end, float rounding)
[SpellInfo](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellInfo%2019fa9a4105a641cfa131dd16b5ac5ab7.md) GetSpellInfo(string spellname)
GetHpBarPos(GameObject obj)

--Vector2 Calculation
Vector3 Clamp2D(Vector3 vec, float max)
bool IsLeft(Vector2 a, Vector2 b, Vector2 c) 
bool PointOnLineSegment(Vector2 pt1, Vector2 pt2, Vector2 pt, double epsilon)
bool IsPointOnLineSegment(Vector2 point, Vector2 start, Vector2 end)

--Player Actions
IssueMove(Vector2 movePos)
MoveToCursor()
IssueAttack(GameObject unit)
-- 0=Q, 1=W, 2 = E...
CastSpellAtPos(int slot, Vector3 castPos)
WasKeyPressed(int key) -- [CLICK HERE FOR KEYCODES](https://www.millisecond.com/support/docs/current/html/language/scancodes.htm)
IsKeyDown(int key) -- [CLICK HERE FOR KEYCODES](https://www.millisecond.com/support/docs/current/html/language/scancodes.htm)
Vector2 GetCursor()

--Damage Calculation
float CalculatePhysicalDamage(float flatDamage, bool shouldCalculateOnHit, GameObject caster, GameObject target)

-- THIS STILL NEEDS WORK!
float CalculateMagicalDamage(float flatDamage, bool shouldCalculateOnHit, GameObject caster, GameObject target)
```

## UI Functions

## Functions

```cpp
void Begin(string name)
void End()
bool Button(string name)
bool ColorButton(string text, Color color)
Vector4 ColorPicker((string text, Color color)
bool Checkbox(string text, Color color)
void Text(string text)
void TextColored((string text, Color color)
void LabelText(string label, string text)
void LabelTextColored(string label, string text, Color color)
void Separator()
int DragInt(string text, int value)
float DragFloat(string text, float value)
int KeySelect(string label, int key)
float SliderFloat(string label, float val, float valMin, float valMax)
int SliderInt(stringlabel, int val, int valMin, int valMax)

bool CollapsingHeader(string text)
bool TreeNode(string text)
void TreePop()
void SetNextItemOpen()
void SameLine()
void BeginGroup()
void EndGroup()

int ListBox(string label, list items, int chosen)
```

## Config Functions

## Functions

```cpp
int GetInt(string key, int defaultVal);
bool GetBool(string key, bool defaultVal);
float GetFloat(string key, float defaultVal);
std::string GetStr(string key, string defaultVal);

void SetInt(string key, int val);
void SetBool(string key, bool val);
void SetFloat(string key, float val);
void SetStr(string key, string val);
```

---

## **Vector Classes and Colors**

## Color

## Properties

```cpp
float red
float green
float blue
float alpha
```

```cpp
Color()
Color(float r,float g,float b,float a)

LOL() -- Typical "League of Legends Yellow Color"
BLACK()
WHITE()
RED()
DARK_RED()
GREEN()
DARK_GREEN()
YELLOW()
DARK_YELLOW()
CYAN()
PURPLE
GRAY()
ORANGE()
BLUE()
BROWN()
```

## Vector2

## Properties

```cpp
float x
float y
```

```cpp
Vector2()
Vector(float x, float y)
float Length()
Vector2 Normalize()
Vector2 Distance(Vector2 to)
Vector2 Scale(float s)
Vector2 VScale(Vector2 s)
Vector2 Add(Vector2 toAdd)
Vector2 Sub(Vector2 ToSub)
Vector2 Clone()
```

## Vector3

## Properties

```cpp
float x
float y
float z
```

```cpp
Vector3()
Vector(float x, float y)
float Length()
Vector3 Normalize()
Vector3 Distance(Vector3 to)
Vector3 Scale(float s)
Vector3 VScale(Vector3 s)
Vector3 Add(Vector3 toAdd)
Vector3 Sub(Vector3 ToSub)
Vector3 Clone()
```

## Vector4

## Properties

```cpp
float x
float y
float z
float w
```

```cpp
Vector4()
Vector(float x, float y)
float Length()
Vector4 Normalize()
Vector4 Distance(Vector4 to)
Vector4 Scale(float s)
Vector4 VScale(Vector4 s)
Vector4 Add(Vector4 toAdd)
Vector4 Sub(Vector4 ToSub)
Vector4 Clone()
```

---

## **GameObject**

### **General Properties and Functions for all GameObjects**

## Properties

```lua
address
health
mana
max_mana
max_health
mana_regen
health_regen
experience
base_atk
bonus_atk
lethality
percent_armorpen
armor
magic_resist
movement_speed
is_alive
name
pos
prev_pos
is_visible
last_visible_at
id
net_id
crit
crit_multi
ap
atk_speed
base_atk_speed
atk_speed_multi
bounding_radius
windup_time
missile_speed
base_movement_speed
team
is_targetable
is_direction
is_invulnerable
is_recalling
atk_range
current_dash_speed
is_dashing
is_moving
dash_pos
nav_begin
nav_end
server_pos
```

## Functions

```cpp
bool HasUnitTag([UnitTag](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/UnitTag%20e331164ee6c04463b778127afab7c541.md) tag) const;

float GetAcquisitionRadius() const;
float GetSelectionRadius() const;
float GetPathingRadius() const;
float GetGameplayRadius() const;

float GetBasicAttackMissileSpeed() const;
float GetBasicAttackWindup() const;

float GetAttackSpeedRatio() const;
float GetBaseMovementSpeed() const;
float GetBaseAttackSpeed() const;
float GetBaseAttackRange() const;
float GetAttackRange() const;
float GetHpBarHeight() const;

bool IsEnemyTo(const GameObject& other) const;
bool IsAllyTo(const GameObject& other) const;
bool IsEqualTo(const GameObject& other) const;
bool IsNotEqualTo(const GameObject& other) const;

bool IsRanged();
float GetBasicAttackDamage();

**-- Hashes can be gathered through the Developer Plugin!
-- Use HasBuff with passing the Hash as parameter, it's faster.!**
bool HasBuff(ULONG hash);
bool HasBuffString(string buffName);
****[BuffInstance](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/BuffInstance%20e5bb64ebbc6b44e89e61f419de35b5e0.md) GetBuff(ULONG hash); 
```

## Example

```lua
function GetAttackSpeed(core)

	if(core:GetPlayer():GetBasicAttackWindup() > 0.2) then
		return core:GetPlayer().atk_speed
	end

	return 0

end
```

### Champion

## Properties

```lua
int level
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) Q
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) W
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) E
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) R
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) D
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) F
```

### Functions

```cpp
bool HasItem(int itemID);
[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md) GetSummonerSpell([SummonerSpellType](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SummonerSpellType%20b8e61f5b3d9042c9b8fbe5f77fac447b.md) type)
```

### Missiles

### Properties

```cpp
int src_index
Vec3 dest_index
Vec3 start_pos
Vec3 end_pos
```

```lua
float GetWidth() const
float GetCastRadius() const
float GetDelay() const
float GetHeight() const
float GetTravelTime() const
std::string GetIcon() const
```

# Enums

[SummonerSpellType](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SummonerSpellType%20b8e61f5b3d9042c9b8fbe5f77fac447b.md)

[MapObject](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/MapObject%207a9dabe8c967467e92625fda3dc4a6bf.md)

[SpellSlot](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellSlot%207587412fd5a343aaadfa49384c8f817c.md)

[SpellInfo](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/SpellInfo%2019fa9a4105a641cfa131dd16b5ac5ab7.md)

[UnitTag](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/UnitTag%20e331164ee6c04463b778127afab7c541.md)

[BuffInstance](League8%20-%20SDK%20Documentation%201a9de27ae2a14c4eb053c21a53e109e9/BuffInstance%20e5bb64ebbc6b44e89e61f419de35b5e0.md)
