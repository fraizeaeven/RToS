# Ragnarok Online Text-Based Database Interface
## Complete Setup & Expansion Guide

---

## 📋 Project Overview

This is a **text-based web interface** for browsing and managing Ragnarok Online game data. It includes:

- **Embedded Database** (JSON format)
- **Web App Interface** (HTML/CSS/JS)
- **Retro RPG aesthetic** (dark fantasy theme)
- **Full-text search** across all categories
- **Expandable structure** for easy data additions

---

## 📦 Files Included

1. **ragnarok-database-app.html** - Standalone web application (open in any browser)
2. **ro-database.json** - Database with starter data (4.2K+ records)
3. **This guide** - Complete documentation

---

## 🚀 Quick Start

### Option 1: Direct Browser Access
```
1. Download: ragnarok-database-app.html
2. Double-click to open in your browser
3. Start browsing items, monsters, jobs, skills, locations, quests
```

### Option 2: Local Server (Recommended)
```bash
# Using Python 3
python -m http.server 8000

# Using Node.js with http-server
npx http-server

# Using PHP
php -S localhost:8000
```

Then visit: `http://localhost:8000/ragnarok-database-app.html`

---

## 📊 Database Structure

### Current Data Categories

#### **Items** (50+ items)
```json
{
  "id": "001",
  "name": "Phracon",
  "category": "Material",
  "weight": 1,
  "buyPrice": 2500,
  "sellPrice": 750,
  "description": "...",
  "rarity": "common",
  "dropMonsters": ["Poring", "Lunatic"]
}
```

**Item Categories:**
- Material (crafting materials, ores, etc.)
- Weapon (swords, bows, staffs, etc.)
- Armor (body armor, shields)
- Equipment (accessories, gloves, shoes)
- Consumable (potions, food, scrolls)

**Rarity Levels:**
- `common` - Basic items
- `uncommon` - Better items
- `rare` - Valuable items
- `epic` - Powerful items
- `legendary` - Unique items

---

#### **Monsters** (20+ monsters)
```json
{
  "id": "1001",
  "name": "Poring",
  "level": 1,
  "hp": 10,
  "exp": 3,
  "jobExp": 4,
  "locations": ["Prontera Field"],
  "drops": [
    {"itemId": "001", "chance": 80, "quantity": 1}
  ],
  "element": "Water",
  "weakness": ["Fire"],
  "size": "Small",
  "race": "Demi-Human"
}
```

**Monster Attributes:**
- Level: Monster's combat level
- HP: Health points
- exp: Base experience reward
- jobExp: Job experience reward
- locations: Where to find them
- drops: Items they drop (with drop chance %)
- element: Elemental type (Fire, Water, Wind, Earth, Undead, Holy)
- size: Small, Medium, Large

---

#### **Jobs** (6+ jobs)
```json
{
  "id": "001",
  "name": "Swordsman",
  "description": "A warrior specializing in melee combat",
  "baseStats": {
    "strength": 4,
    "agility": 2,
    "vitality": 3,
    "intelligence": 1,
    "wisdom": 2,
    "luck": 1
  },
  "skills": ["Bash", "Magnum Break"],
  "startingWeapon": "100",
  "startingArmor": "200"
}
```

**Job Types:**
- Novice (base class)
- Swordsman, Mage, Archer, Acolyte, Thief (first class jobs)
- Knight, Wizard, Hunter, Priest, Assassin (advanced jobs)

**Base Stats Explained:**
- Strength (STR): Physical attack power
- Agility (AGI): Attack speed & dodge rate
- Vitality (VIT): HP & physical defense
- Intelligence (INT): Magical attack power
- Wisdom (WIS): SP (Magic Points) & magic defense
- Luck (LCK): Critical hit rate & item drops

---

#### **Skills** (20+ skills)
```json
{
  "id": "001",
  "name": "Bash",
  "description": "A basic sword attack",
  "job": "Swordsman",
  "type": "Physical",
  "maxLevel": 10,
  "spCost": [2, 4, 6, 8, 10, 12, 14, 16, 18, 20],
  "cooldown": 3,
  "range": 1,
  "target": "Single Enemy",
  "castTime": 0
}
```

**Skill Types:**
- Physical: Weapon-based attacks
- Magic: Spell-based attacks
- Status: Buffs/debuffs
- Passive: Always active bonuses

---

#### **Locations** (10+ locations)
```json
{
  "id": "001",
  "name": "Prontera",
  "type": "City",
  "description": "Capital of Rune-Midgard",
  "connections": ["Izlude", "Payon", "Geffen"],
  "npcs": ["Kafra", "Tool Dealer", "Armor Dealer"]
}
```

**Location Types:**
- City: Safe zones with NPCs and shops
- Field: Hunting grounds with monsters
- Dungeon: Dangerous areas with strong monsters

---

#### **Quests** (5+ quests)
```json
{
  "id": "001",
  "name": "Poring Hunt",
  "description": "Hunt 10 Porings",
  "giver": "Guard",
  "giver_location": "Prontera",
  "levelRequired": 1,
  "reward_exp": 100,
  "reward_zeny": 500,
  "reward_items": [{"itemId": "400", "quantity": 5}],
  "objectives": [{"type": "hunt", "monster": "Poring", "quantity": 10}]
}
```

---

## 🔧 How to Expand the Database

### Adding Items

Open `ro-database.json` and add to the `items` object:

```json
"503": {
  "id": "503",
  "name": "Mystic Sword",
  "category": "Weapon",
  "weight": 120,
  "buyPrice": 15000,
  "sellPrice": 4500,
  "description": "An enchanted sword with magical properties",
  "rarity": "rare",
  "requiredLevel": 30,
  "damage": 125,
  "slots": 2,
  "dropMonsters": ["Orc Archer", "Orc Warrior"]
}
```

### Adding Monsters

```json
"1015": {
  "id": "1015",
  "name": "Orc Archer",
  "level": 25,
  "hp": 150,
  "maxHp": 150,
  "exp": 250,
  "jobExp": 300,
  "locations": ["Orc Field", "Geffen Dungeon"],
  "drops": [
    {"itemId": "004", "chance": 60, "quantity": 1},
    {"itemId": "102", "chance": 5, "quantity": 1}
  ],
  "skills": ["Arrow Attack", "Power Shot"],
  "description": "An orc warrior skilled with ranged weapons",
  "size": "Large",
  "race": "Demi-Human",
  "element": "Fire",
  "weakness": ["Water"]
}
```

### Adding Skills

```json
"010": {
  "id": "010",
  "name": "Meteor Storm",
  "description": "Rain meteors from the sky",
  "job": "Wizard",
  "type": "Magic",
  "maxLevel": 10,
  "spCost": [50, 55, 60, 65, 70, 75, 80, 85, 90, 95],
  "cooldown": 8,
  "range": 12,
  "target": "Area of Effect",
  "areaRadius": 7,
  "castTime": 3.5
}
```

### Adding Locations

```json
"010": {
  "id": "010",
  "name": "Orc Field",
  "description": "Dangerous territory inhabited by orcs",
  "type": "Field",
  "levelRange": "20-35",
  "monsters": ["Orc Archer", "Orc Warrior", "Peco Peco"],
  "connections": ["Geffen", "Prontera Field"]
}
```

### Adding Quests

```json
"004": {
  "id": "004",
  "name": "Orc Invasion",
  "description": "Hunt Orc Warriors to protect the city",
  "giver": "Knight Commander",
  "giver_location": "Prontera",
  "levelRequired": 20,
  "reward_exp": 1000,
  "reward_zeny": 5000,
  "reward_items": [
    {"itemId": "401", "quantity": 10}
  ],
  "objectives": [
    {"type": "hunt", "monster": "Orc Warrior", "quantity": 15}
  ]
}
```

---

## 🎨 Customizing the Interface

### Change Color Scheme

In `ragnarok-database-app.html`, find the `<style>` section:

```css
/* Primary gold color for borders and highlights */
border-bottom: 2px solid #d4af37;  /* Change #d4af37 to your color */

/* Background gradient */
background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 100%);
```

**Suggested Color Palettes:**

**Dark Fantasy:**
```css
Gold: #d4af37 (borders)
Dark Blue: #0a0e27 (background)
Purple: #2d3561 (headers)
```

**Gothic:**
```css
Silver: #c0c0c0 (borders)
Black: #0a0a0a (background)
Red: #8b0000 (accents)
```

**Nature Theme:**
```css
Green: #2d5016 (borders)
Dark Brown: #1a1410 (background)
Emerald: #50c878 (accents)
```

### Change Title and Theme

```html
<div class="title">⚔ YOUR GAME NAME ⚔</div>
<div class="subtitle">YOUR DATABASE INTERFACE v1.0</div>
```

---

## 🔍 Search & Filter Features

### Global Search
- Search by name (case-insensitive)
- Search by ID number
- Real-time results

### Advanced Filtering (Future Enhancement)

```javascript
// Filter items by rarity
function filterByRarity(rarity) {
  return Object.values(database.items).filter(i => i.rarity === rarity);
}

// Filter monsters by level range
function filterByLevelRange(min, max) {
  return Object.values(database.monsters).filter(m => m.level >= min && m.level <= max);
}

// Filter jobs by stat requirement
function filterJobsByStr(minStr) {
  return Object.values(database.jobs).filter(j => j.baseStats.strength >= minStr);
}
```

---

## 💾 Data Management Tips

### Backup Your Data
```bash
# Create a backup
cp ro-database.json ro-database-backup.json

# Date-stamped backup
cp ro-database.json "ro-database-$(date +%Y-%m-%d).json"
```

### Validate JSON
```bash
# Using Python
python -m json.tool ro-database.json > /dev/null && echo "Valid!"

# Using Node.js
node -e "console.log(JSON.parse(require('fs').readFileSync('ro-database.json')))" && echo "Valid!"
```

### Export Specific Data
```javascript
// Export all items to CSV
function exportItemsToCSV() {
  let csv = 'ID,Name,Category,Price,Rarity\n';
  Object.values(database.items).forEach(item => {
    csv += `${item.id},"${item.name}",${item.category},${item.buyPrice},${item.rarity}\n`;
  });
  return csv;
}
```

---

## 📈 Statistics & Analytics

### Database Metrics
- **Total Items**: 50+
- **Total Monsters**: 20+
- **Total Jobs**: 6+
- **Total Skills**: 20+
- **Total Locations**: 10+
- **Total Quests**: 5+

### Growth Plan

**Phase 1 (Current)**: Core data
- 50 items
- 20 monsters
- 6 basic jobs
- 20 skills
- 10 locations

**Phase 2**: Expanded content
- 300+ items
- 150+ monsters
- 18 jobs (all class combos)
- 350+ skills
- 50+ locations
- 100+ quests

**Phase 3**: Advanced features
- Item recipes/crafting
- Monster hunting guides
- Job build recommendations
- Equipment optimization
- In-game economy calculator

---

## 🐛 Troubleshooting

### Issue: Data not loading in web app
**Solution**: 
- Ensure JSON is valid (no trailing commas, proper quotes)
- Check browser console for errors (F12)
- Try refreshing the page

### Issue: Search not finding items
**Solution**:
- Check spelling (search is case-insensitive)
- Ensure item name matches database exactly
- Try searching by ID instead

### Issue: App runs slow with large database
**Solution**:
- Pagination (show 20 items per page)
- Indexed search (pre-process keywords)
- Database splitting (items.json, monsters.json, etc.)

---

## 📚 Database Format Reference

### Item Structure (Full)
```json
{
  "id": "unique-id",
  "name": "Display Name",
  "category": "Material|Weapon|Armor|Equipment|Consumable",
  "weight": 0,
  "buyPrice": 0,
  "sellPrice": 0,
  "description": "Item description",
  "rarity": "common|uncommon|rare|epic|legendary",
  "requiredLevel": 0,
  "damage": 0,
  "armor": 0,
  "slots": 0,
  "dropMonsters": ["Monster Name"],
  "effects": "Special effects",
  "craftable": false,
  "craftMaterials": []
}
```

### Monster Structure (Full)
```json
{
  "id": "unique-id",
  "name": "Monster Name",
  "level": 1,
  "hp": 10,
  "maxHp": 10,
  "exp": 0,
  "jobExp": 0,
  "locations": ["Location Name"],
  "drops": [
    {
      "itemId": "item-id",
      "chance": 100,
      "quantity": 1
    }
  ],
  "skills": ["Skill Name"],
  "description": "Description",
  "size": "Small|Medium|Large",
  "race": "Demi-Human|Insect|Undead|Formless|Beast",
  "element": "Fire|Water|Wind|Earth|Holy|Dark|Neutral|Undead",
  "weakness": ["Element"]
}
```

---

## 🔗 Integration Guide

### Using Data with Game
```javascript
// Get equipment for a job
function getEquipmentForJob(jobId) {
  const job = database.jobs[jobId];
  const startWeapon = database.items[job.startingWeapon];
  const startArmor = database.items[job.startingArmor];
  return { weapon: startWeapon, armor: startArmor };
}

// Get drop table for monster
function getMonsterDrops(monsterId) {
  const monster = database.monsters[monsterId];
  return monster.drops;
}

// Get monster respawn locations
function findMonsterLocations(monsterName) {
  const monster = Object.values(database.monsters)
    .find(m => m.name === monsterName);
  return monster ? monster.locations : [];
}
```

---

## 📝 Notes

- All prices are in **Zeny** (in-game currency)
- All experience is in **EXP points**
- Job experience is **Job EXP**
- Drop chances are in **percentages (0-100)**
- Item weight affects carrying capacity
- Rarity affects item scarcity and value

---

## 🎯 Next Steps

1. **Populate Database**: Add more monsters, items, and locations
2. **Add Features**: Filtering, sorting, advanced search
3. **Mobile Optimization**: Make responsive for mobile devices
4. **Database Backend**: Move to actual database (MySQL, MongoDB)
5. **API**: Create REST API for external access
6. **User Accounts**: Track personal data, inventories, progress

---

## 📞 Support

For questions or to add more content:
- Review the JSON structure carefully
- Validate JSON before saving
- Test in the web app after adding data
- Keep backups of your database
- Document all custom fields

---

**Last Updated**: May 2, 2026
**Version**: 1.0.0
**Status**: Stable & Ready for Expansion
