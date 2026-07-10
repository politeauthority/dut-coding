# Level 5: Loops & Loot 🔁

**Goal:** Make the computer do things thousands of times without complaining (loops), and
store collections of stuff (lists and dictionaries). This is the level where programs
start feeling *powerful*.

## The concepts

```python
# while — repeat as long as something is true
hp = 100
while hp > 0:
    print(f"Still alive with {hp} HP")
    hp = hp - 25          # without this line: INFINITE LOOP (Ctrl+C to escape!)

# for + range — repeat an exact number of times
for i in range(5):        # i = 0, 1, 2, 3, 4  (starts at 0!)
    print(f"Wave {i} of enemies incoming")

# lists — an ordered backpack, slots numbered from 0
inventory = ["sword", "shield", "potion"]
print(inventory[0])           # sword
inventory.append("map")       # add to the end
inventory.remove("potion")    # used it!
print(len(inventory))         # how many items?

for item in inventory:        # loop over every item
    print(f"You are carrying: {item}")

# dictionaries — a chest with labeled compartments
player = {"name": "Alex", "hp": 100, "coins": 50}
print(player["coins"])        # 50
player["coins"] += 10         # found gold!
player["level"] = 2           # new label, new value
```

## Core Quests

1. **Upgrade `number_guess.py`.** Unlimited guesses with a `while` loop, count the number
   of guesses, and print it when they win. Then the finishing move: at the top, add
   `import random` and `secret = random.randint(1, 100)` — now even YOU don't know the
   answer. Congratulations, you just used your first module.
2. **`inventory.py`** — a loop that shows a menu over and over: `1) show inventory
   2) pick up item  3) drop item  4) quit`. Use a list. Bonus polish: what happens if
   they drop an item they don't have?
3. **`shop.py`** — the big one. A dictionary of items and prices (`{"sword": 50,
   "potion": 10, ...}`), the player starts with 100 coins, a loop lets them buy items
   until they quit or run out of coins. Print their remaining coins and what they own at
   the end. **Sketch it on paper before coding** — what are the steps each time through
   the loop?
4. **`times_table.py`** — ask for a number, print its times table from 1 to 12 using a
   `for` loop. Short, but make the output neat.
5. **Notes** (`level-05.md`): in your own words — when do you use a `while` vs a `for`?
   When a list vs a dictionary? Plus questions. Keep the commit streak: 6+ commits.

## Side Quests

- Make the shop refuse to sell you something you already own.
- Nested data, sneak peek: make `player["inventory"]` a LIST inside the dictionary.
  Mind = blown? That's how real game data looks.
- `for i in range(10, 0, -1)` — what does this do? Use it to build a rocket-launch
  countdown.

## 🎮 Roblox Connection

Dictionaries are THE data shape of Roblox. Every player's data in a real Roblox game —
coins, inventory, pets, level — is stored as a table (Luau's version of a dictionary):

```lua
local player = {name = "Alex", hp = 100, coins = 50}   -- looks familiar?
```

Your `shop.py` is, no joke, the core logic of every Roblox tycoon game ever made.
