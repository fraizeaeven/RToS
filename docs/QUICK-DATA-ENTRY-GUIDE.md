# Ragnarok Online Database - Quick Data Entry Guide

## 📋 Copy & Paste Templates

Use these templates to quickly add new data to your `ro-database.json` file.

---

## 🎁 ADD NEW ITEM

```json
"504": {
  "id": "504",
  "name": "Item Name Here",
  "category": "Material",
  "weight": 10,
  "buyPrice": 5000,
  "sellPrice": 1500,
  "description": "Item description",
  "rarity": "uncommon",
  "dropMonsters": ["Monster Name"]
}
```

**Fields to Change:**
- `504` → Unique ID number (use next available)
- `Item Name Here` → Your item name
- `Material` → Category: Material, Weapon, Armor, Equipment, Consumable
- `10` → Weight in zeny units
- `5000` → NPC buy price
- `1500` → NPC sell price
- `uncommon` → Rarity: common, uncommon, rare, epic, legendary

**Optional Fields for Weapons:**
```json
"requiredLevel": 10,
"damage": 50,
"slots": 1,
"type": "One-Handed Sword"
```

**Optional Fields for Armor:**
```json
"requiredLevel": 10,
"armor": 15,
"slots": 1,
"type": "Plate Armor"
```

**Optional Fields for Consumables:**
```json
"effect": "healHP",
"effectValue": 150,
"stackable": true
```

---

## 👹 ADD NEW MONSTER

```json
"1020": {
  "id": "1020",
  "name": "Monster Name",
  "level": 15,
  "hp": 100,
  "maxHp": 100,
  "exp": 500,
  "jobExp": 600,
  "locations": ["Location Name", "Another Location"],
  "drops": [
    { "itemId": "001", "chance": 50, "quantity": 1 },
    { "itemId": "002", "chance": 30, "quantity": 2 }
  ],
  "skills": ["Attack Name"],
  "description": "Monster description",
  "size": "Medium",
  "race": "Demi-Human",
  "element": "Fire",
  "weakness": ["Water"]
}
```

**Fields to Change:**
- `1020` → Unique monster ID (1000+)
- `Monster Name` → Name of the monster
- `15` → Monster level
- `100` → Monster health points
- `500` → Base experience reward
- `600` → Job experience reward
- `Location Name` → Where players find this monster
- `Fire` → Element type
- `Water` → What it's weak to

**Element Types:**
- Fire (weak to Water)
- Water (weak to Lightning)
- Wind (weak to Earth)
- Earth (weak to Wind)
- Holy (weak to Dark)
- Dark (weak to Holy)
- Neutral (no weakness)
- Undead (weak to Fire, Holy)

**Size Types:**
- Small (Poring, Thief Bug)
- Medium (Rocker, Archer Skeleton)
- Large (Mummy, Manouk)

**Race Types:**
- Demi-Human (humanoid monsters)
- Insect (bugs, spiders)
- Undead (skeletons, zombies)
- Formless (blobs, golems)
- Beast (animals, wolves)
- Plant (trees, moving plants)
- Dragon (dragon type)
- Fish (aquatic creatures)

---

## 💼 ADD NEW JOB

```json
"007": {
  "id": "007",
  "name": "Knight",
  "description": "An advanced warrior with sword mastery",
  "baseStats": {
    "strength": 5,
    "agility": 3,
    "vitality": 4,
    "intelligence": 1,
    "wisdom": 2,
    "luck": 1
  },
  "skills": ["Slash", "Pecopeco Ride", "Brandish Spear"],
  "startingWeapon": "101",
  "startingArmor": "201",
  "requiredLevel": 10,
  "prerequisiteJob": "002"
}
```

**Fields to Change:**
- `007` → Unique job ID
- `Knight` → Job name
- `strength: 5` → Base stat values (1-10 scale)
- `skills` → List of job skills
- `101` → Item ID for starting weapon
- `201` → Item ID for starting armor
- `10` → Level required to advance to this job
- `002` → ID of prerequisite job (optional)

**Base Stats Guide:**
- Strength: Increases physical damage (Swordsman, Knight)
- Agility: Increases attack speed & dodge (Archer, Thief)
- Vitality: Increases HP & defense (Knight, Swordsman)
- Intelligence: Increases magic damage (Mage, Wizard)
- Wisdom: Increases HP recovery & magic defense (Acolyte, Priest)
- Luck: Increases critical hits & item drops (Thief)

---

## 🔮 ADD NEW SKILL

```json
"011": {
  "id": "011",
  "name": "Skill Name",
  "description": "What the skill does",
  "job": "Swordsman",
  "type": "Physical",
  "maxLevel": 10,
  "spCost": [20, 22, 24, 26, 28, 30, 32, 34, 36, 38],
  "cooldown": 4,
  "range": 1,
  "target": "Single Enemy",
  "castTime": 0
}
```

**Fields to Change:**
- `011` → Unique skill ID
- `Skill Name` → Skill name
- `Swordsman` → Job that learns this skill
- `Physical` → Type: Physical, Magic, Status, Passive
- `10` → Maximum skill level
- `[20,22,24...]` → SP cost for each level (must have 10 values for level 10)
- `4` → Cooldown in seconds
- `1` → Range in tiles (1=melee, 5+=ranged)
- `Single Enemy` → Target type

**Skill Types:**
- Physical (weapon-based attacks)
- Magic (spell-based attacks)
- Status (buffs/debuffs)
- Passive (always active)

**Target Types:**
- Single Enemy
- Single Ally
- Area of Effect (enemies in radius)
- Self
- Party (all allies)

**Range Guide:**
- 1 = Melee (adjacent)
- 3-5 = Close ranged
- 7-9 = Medium ranged
- 10+ = Long ranged

---

## 🗺️ ADD NEW LOCATION

```json
"012": {
  "id": "012",
  "name": "Location Name",
  "type": "Field",
  "description": "What players find here",
  "levelRange": "20-35",
  "monsters": ["Monster Name 1", "Monster Name 2"],
  "connections": ["Connected Location 1", "Connected Location 2"],
  "npc": ["NPC Name"]
}
```

**Fields to Change:**
- `012` → Unique location ID
- `Location Name` → Location name
- `Field` → Type: City, Field, Dungeon, Cave
- `20-35` → Recommended level range
- `Monster Name` → Monsters found here
- `Connected Location` → Adjacent areas

**Location Types:**
- City (safe, has shops/NPCs)
- Field (outdoor hunting ground)
- Dungeon (underground, dangerous)
- Cave (cavern area)

---

## 📜 ADD NEW QUEST

```json
"004": {
  "id": "004",
  "name": "Quest Name",
  "description": "What players need to do",
  "giver": "NPC Name",
  "giver_location": "Location Name",
  "levelRequired": 10,
  "reward_exp": 1000,
  "reward_zeny": 5000,
  "reward_items": [
    { "itemId": "001", "quantity": 5 }
  ],
  "objectives": [
    { "type": "hunt", "monster": "Monster Name", "quantity": 10 }
  ]
}
```

**Fields to Change:**
- `004` → Unique quest ID
- `Quest Name` → Quest title
- `NPC Name` → Quest giver
- `Location Name` → Where to find quest giver
- `10` → Minimum level to accept quest
- `1000` → Experience reward
- `5000` → Zeny (money) reward
- `itemId: "001"` → Reward item (use item IDs)
- `Monster Name` → Target for hunt quests

**Objective Types:**
- hunt: Kill X monsters
- collect: Gather X items
- talk: Speak with NPC
- travel: Visit location
- craft: Create item

---

## 🔄 ADDING DROP TABLES

When adding monster drops, use this format:

```json
"drops": [
  { "itemId": "001", "chance": 100, "quantity": 1 },
  { "itemId": "002", "chance": 50, "quantity": 2 },
  { "itemId": "003", "chance": 10, "quantity": 1 }
]
```

**Chance Value Guide:**
- 100 = Always drops (common items)
- 50 = 50% chance (uncommon items)
- 20 = 20% chance (rare items)
- 5 = 5% chance (very rare)
- 1 = 1% chance (extremely rare)

---

## 📊 BATCH DATA ENTRY

### Add Multiple Items at Once

```json
"505": { "id": "505", "name": "Leather Strap", "category": "Equipment", "weight": 8, "buyPrice": 1200, "sellPrice": 360, "rarity": "common" },
"506": { "id": "506", "name": "Silk Robe", "category": "Equipment", "weight": 15, "buyPrice": 3000, "sellPrice": 900, "rarity": "uncommon" },
"507": { "id": "507", "name": "Wool Scarf", "category": "Equipment", "weight": 5, "buyPrice": 800, "sellPrice": 240, "rarity": "common" }
```

**Tips:**
- Keep each entry on one line for batch edits
- Use commas between entries
- Last entry should NOT have a trailing comma
- Always validate JSON after bulk edits

---

## ✅ VALIDATION CHECKLIST

Before adding data, verify:

- [ ] ID is unique (not used elsewhere)
- [ ] All required fields are filled
- [ ] Prices are positive numbers
- [ ] Text doesn't have unescaped quotes
- [ ] Arrays are properly formatted [ ]
- [ ] Objects are properly formatted { }
- [ ] No trailing commas at end of objects
- [ ] Rarity is valid (common, uncommon, rare, etc)
- [ ] Element type is valid
- [ ] Numbers for IDs match database format
- [ ] Description is descriptive but brief
- [ ] JSON validates in online JSON checker

---

## 🔗 LINKING DATA RELATIONSHIPS

When adding related items:

**Monster → Items (Drops)**
```json
// In monster drops
{ "itemId": "001", "chance": 60, "quantity": 1 }
// This references item ID "001" from items table
```

**Job → Skills**
```json
// In job
"skills": ["Bash", "Magnum Break"]
// These must match skill names in skills table
```

**Job → Equipment**
```json
// In job
"startingWeapon": "100"
"startingArmor": "200"
// These must be valid item IDs
```

**Monster → Location**
```json
// In monster
"locations": ["Prontera Field", "Mjolnir Field"]
// These must match location names
```

---

## 💡 TIPS & TRICKS

### Generate IDs Automatically
```javascript
// Find next available item ID
let maxId = Math.max(...Object.keys(database.items).map(Number));
let nextId = (maxId + 1).toString().padStart(3, '0');
```

### Price Formula
```
Sell Price = Buy Price ÷ 3 (approximately)
Example: Buy 3000 → Sell 1000

For rare items:
Sell Price = Buy Price ÷ 4 (higher markup)
```

### Experience Progression
```
Level 1 monster: 3 exp
Level 5 monster: 15 exp (×5)
Level 10 monster: 40 exp (×2.6)
Level 15 monster: 75 exp (×1.9)
```

### Drop Chance Formula
```
Common items (100% or 80%): Always drop
Uncommon (50-60%): Often drop
Rare (20-30%): Sometimes drop
Very Rare (5-10%): Rarely drop
Legendary (<5%): Extremely rare
```

---

## 🐛 COMMON MISTAKES

❌ **Trailing comma**
```json
{ "id": "1", "name": "Test", } // WRONG - comma after last field
```

✅ **Correct**
```json
{ "id": "1", "name": "Test" } // CORRECT
```

❌ **Unescaped quotes**
```json
"description": "An item that's "special"" // WRONG
```

✅ **Correct**
```json
"description": "An item that's \"special\"" // CORRECT - escaped quotes
```

❌ **Missing brackets**
```json
"drops": { "itemId": "001" } // WRONG - drops is array
```

✅ **Correct**
```json
"drops": [{ "itemId": "001" }] // CORRECT - array of objects
```

---

## 📚 QUICK REFERENCE IDS

### Item ID Ranges
- 001-099: Materials
- 100-199: Weapons
- 200-299: Armor
- 300-399: Equipment
- 400-499: Consumables
- 500+: New additions

### Monster ID Ranges
- 1001-1099: Small monsters
- 1100-1199: Medium monsters
- 1200-1299: Large monsters
- 1300+: Bosses

### Job ID Ranges
- 001-099: Base jobs
- 100-199: First class jobs
- 200-299: Advanced jobs

### Skill ID Ranges
- 001-099: Physical skills
- 100-199: Magic skills
- 200-299: Support skills
- 300+: Passive abilities

---

**Last Updated**: May 2, 2026
**Version**: 1.0.0
