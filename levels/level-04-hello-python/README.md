# Level 4: Hello, Python 🐍

**Goal:** Write your first real programs. Python is one of the most-used languages in the
world — it runs YouTube, Instagram, NASA tools, and AI systems. It's also the friendliest
language to learn first.

## The concepts

```python
# variables — labeled boxes that hold values
player_name = "Alex"        # a string (text)
health = 100                # an integer (whole number)
speed = 16.5                # a float (decimal)
is_alive = True             # a boolean (True/False)

# printing with f-strings — put variables inside text
print(f"{player_name} has {health} HP")

# input — ask the user something (always comes back as a STRING)
age = int(input("How old are you? "))   # int(...) converts to a number

# decisions
if health <= 0:
    print("Game over!")
elif health < 30:
    print("Low health, find a heal!")
else:
    print("You're fine, keep going")
```

Notice the **indentation** — Python uses the spacing to know what's inside the `if`.
It's not decoration; it's the law.

## Core Quests

All files go in `python/`, committed and pushed as you go (keep the streak — 6+ commits).

1. **`about_me.py`** — prints 5 lines about you using at least 3 variables and f-strings.
2. **`age_bot.py`** — asks for a birth year and prints how old you'll turn this year, and
   how old you'll be in 2050. (Careful: `input()` gives you a string!)
3. **`damage_calc.py`** — a game damage calculator: ask for the attack power and the
   target's armor. Damage = attack minus armor, but if armor is higher than attack, print
   "It bounced off!" instead of a negative number.
4. **`number_guess.py`** — the classic: the program picks a secret number (hardcode it
   for now, e.g. `secret = 7`), the player gets ONE guess, and you print "too high",
   "too low", or "you got it!". (Next level, loops give them unlimited guesses.)
5. **Notes** (`level-04.md`): explain in your own words what a variable is, what an
   f-string is, and what the difference is between `"7"` and `7`. Plus your questions.

## Side Quests

- Add a rock-paper-scissors game (`rps.py`) — you vs. a hardcoded computer choice.
- In `age_bot.py`, handle the person typing something that isn't a number... just kidding,
  you can't yet. But run it, type "banana", and READ the error carefully. Write down what
  error type it is. (Level 6 teaches you how to survive this.)

## 🎮 Roblox Connection

Roblox's language, Luau, has the same ideas with slightly different clothes:

| Python | Luau (Roblox) |
|--------|---------------|
| `health = 100` | `local health = 100` |
| `print(f"HP: {health}")` | `print("HP: " .. health)` |
| `if health <= 0:` | `if health <= 0 then ... end` |

Learn it once in Python, and Level 13 will feel like a costume change, not a new game.
