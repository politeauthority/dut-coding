# Level 6: Level Up Your Python 🧰

**Goal:** Functions (your own reusable commands), files (programs that remember), and
error handling (programs that don't explode). Then combine EVERYTHING into your biggest
build yet: a text adventure game.

## The concepts

```python
# functions — teach the computer a new command
def attack(attacker, power):
    print(f"{attacker} attacks with {power} power!")
    return power * 2          # send a value back to whoever called

damage = attack("Alex", 10)   # damage is now 20

# files — write and read
with open("save.txt", "w") as f:     # "w" = write (wipes the file first!)
    f.write("coins: 100")

with open("save.txt", "r") as f:     # "r" = read
    data = f.read()

# errors — catch problems instead of crashing
try:
    guess = int(input("Your guess: "))
except ValueError:
    print("That's not a number, friend.")
```

## Core Quests

1. **Refactor mission.** Go back to `shop.py` and reorganize it with functions:
   `show_menu()`, `buy_item(...)`, etc. The program should work exactly the same —
   improving code without changing behavior is called **refactoring**, and pros do it
   constantly. Commit before AND after so you can `git diff` the improvement.
2. **Bulletproof input.** Write `ask_for_number(question)` — a function that keeps asking
   until the user actually types a number (loop + try/except), then `return`s it. Use it
   in your guess game. This little function is a keeper — you'll reuse it forever.
3. **🏰 THE TEXT ADVENTURE** (`adventure.py`) — your biggest project yet, and it's a
   *terminal obby*. Requirements:
   - At least 5 rooms, stored as a dictionary of dictionaries (each room has a
     description and which rooms it connects to)
   - Commands: `go north/south/east/west`, `look`, `take <item>`, `inventory`, `quit`
   - At least 2 items to pick up, and one door/room that needs an item ("the vault door
     is locked... maybe if you had a key?")
   - A way to win and a way to lose
   - Functions for the major actions — no 200-line blob!
   - **Save/load side of the quest:** on `quit`, write the player's room + inventory to
     `save.txt`; on start, offer to continue.

   Work on this a little every day. Commit every session. This is a 2-week build.
4. **Notes** (`level-06.md`): what does `return` do? What's the difference between `"w"`
   and `"r"` modes? Questions for your mentor.

## Side Quests

- Add a monster to one room that you fight with a dice roll (`random.randint(1, 6)`).
- Add gold + a shopkeeper room (you already wrote a shop... reuse the functions! 😏)
- Make the map bigger. Way bigger.

## 🎮 Roblox Connection

Roblox games are MADE of functions — they're how your game reacts to events:

```lua
local function onTouched(otherPart)
    print("Something touched the lava!")
end
part.Touched:Connect(onTouched)   -- "when touched, run my function"
```

And your save/load file? In Roblox that's called a **DataStore** — same idea (save the
player's stuff, load it when they return), which you'll see in Level 13. Rooms connected
to rooms is also exactly how obby checkpoints work.
