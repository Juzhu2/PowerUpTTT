# Shared-Grid Tactical TCG  
**Design Document (v0.1)**

## 1. Core Concept

A competitive, turn-based trading card game played on a **shared grid board**, where both players summon and control minions in the same spatial environment.  
There is **no player-side ownership of board spaces**—only ownership of minions.

The primary goal is to **reduce the opponent’s health to zero**.

The game blends:
- Auto-scaling resource systems (Hearthstone / Shadowverse)
- Tactical spatial positioning
- Deterministic combat (no blocking by default)
- High interaction through board control rather than reaction timing

---

## 2. Players

- **Number of Players:** 2  
- **Starting Health:** TBD (e.g., 30)  
- **Deck Size:** TBD (e.g., 30–40 cards)  
- **Hand Limit:** TBD (e.g., 10)

Players alternate turns. Only the active player may take actions unless a card explicitly states otherwise.

---

## 3. Board & Grid

### 3.1 Board Layout
- The game board is a **shared rectangular grid** (e.g., 5×5, 6×6 — size TBD).
- Each grid cell may contain **at most one minion**.
- There is **no “your side” or “opponent’s side.”**

### 3.2 Face (Player Avatar)
- Each player has a **Face**, representing their health.
- Faces are **off-grid**.
- Faces may be attacked **globally**, unless restricted by effects (e.g., Taunt).

---

## 4. Resources (Mana System)

### 4.1 Auto-Resource System
- Players gain **1 maximum mana per turn**, up to a cap (e.g., 10).
- Mana refills to maximum at the start of each player’s turn.
- There are **no resource cards** (no lands, no ramp cards unless explicitly designed).

### 4.2 Resource Usage
Mana is spent to:
- Play cards
- Activate abilities
- Perform special actions (if applicable)

---

## 5. Cards & Minions

### 5.1 Card Types
Initial card types:
- **Minions**
- **Spells**
- *(Optional future expansion: Artifacts, Structures, Terrain)*

---

### 5.2 Minion Properties

Each minion has:
- **Owner**
- **Attack**
- **Health**
- **Mana Cost**
- **Keywords / Effects**
- **Grid Position**

---

### 5.3 Summoning Minions

- Minions are summoned onto **any empty grid space**, unless restricted.
- A player may summon **any number of minions per turn**, limited only by:
  - Available mana
  - Available empty grid spaces
  - Card-specific restrictions

---

## 6. Summoning Sickness

- Newly summoned minions gain **Summoning Sickness**.
- A minion with Summoning Sickness:
  - Cannot attack
  - Cannot move
- Summoning Sickness is removed at the **start of the owner’s next turn**, unless stated otherwise.

---

## 7. Movement

- By default, **minions cannot move**.
- Movement must be explicitly granted by:
  - Keywords
  - Activated abilities
  - Spells

This makes **placement decisions permanent and meaningful**.

---

## 8. Combat System

### 8.1 Attacking
- Attacks are **global by default**.
- A minion may attack:
  - Any opposing minion
  - The opponent’s Face

Unless restricted by:
- Taunt
- Wards
- Other effects

---

### 8.2 Trading (Minion vs Minion Combat)

When a minion attacks another minion:
- Both minions deal damage equal to their Attack
- Damage is simultaneous
- Minions reduced to 0 or less Health are destroyed

There is **no blocking**, interception, or reaction unless explicitly stated.

---

### 8.3 Attacking Face

- Attacks against Face deal damage equal to the attacker’s Attack.
- Face does not deal return damage.
- Face attacks may be restricted by effects such as Taunt.

---

## 9. Interaction Rules

### 9.1 Turn Ownership
- Only the active player may take actions during their turn.
- Opponent interaction is **not allowed by default**.

### 9.2 No Blocking
- Defending players cannot block attacks.
- Combat decisions are made entirely by the attacker.

This emphasizes:
- Board control
- Preemptive positioning
- Threat management

---

## 10. Keywords & Mechanics (Initial Set)

### 10.1 Taunt
- While a Taunt minion exists, the opponent **must attack Taunt minions before Face**.
- Taunt does not prevent attacking other minions unless specified.

### 10.2 Ward (Shield / Protection)
- Prevents the next instance of damage to the minion.
- Removed after damage prevention.

### 10.3 Additional Keyword Slots (Future)
- Guard (local restriction)
- Zone Control
- Lockdown
- Overwatch-style triggers
- Terrain modifiers

---

## 11. Board State Limits

- There is **no default board-stall breaker**.
- The board may fully fill with minions.
- Board control is achieved through:
  - Efficient trading
  - Removal spells
  - Forced movement / destruction effects

This allows intentional **stall-based strategies** to exist.

---

## 12. Fatigue / Long Game Resolution

To prevent infinite or excessively long games, a **Fatigue Mechanic** is implemented.

### Example Fatigue Systems (TBD):
- Drawing from an empty deck deals increasing damage (1, 2, 3, …)
- A global “Collapse” turn counter introduces escalating penalties
- Board decay: grid spaces become unusable over time

Exact implementation TBD.

---

## 13. Win Condition

A player wins when:
- The opponent’s **Health reaches 0 or less**

---

## 14. Design Pillars

- **Shared Space = Shared Risk**
- **No Reaction Speed Advantage**
- **Placement Matters More Than Timing**
- **Limited Mobility, High Commitment**
- **Simple Rules → Emergent Complexity**

---

## 15. Notes for Engine Architecture (Optional)

This ruleset maps cleanly to:
- Intent-based action systems
- Event triggers (`OnSummon`, `OnAttack`, `OnDeath`)
- Immutable game-state transitions
- Deterministic resolution order

---
