# CLAUDE.md — Project Instructions

## Project Name
DopeWars-2025

## Project Intent
Build a modern, real-world, asynchronous market & logistics simulation inspired by classic Dope Wars.

This is a **strategy game about time, geography, pressure, and consequence**.

This is NOT:
- A turn-based game
- A real-time PvP game
- A live flight booking app
- A trading simulator with charts everywhere

---

## Non-Negotiable Constraints

- $0 budget
- No paid APIs
- No scraping airline or travel websites
- No live flight booking
- All realism must be **simulated** using open/static data
- iPad-friendly development (browser / VS Code Web)
- Systems must work offline where possible

---

## Core Design Pillars (Never Break These)

1. **Time Is Real**
   - The world runs continuously
   - Markets move whether the player is active or not
   - Travel takes real time

2. **Commitment Has Consequences**
   - When travel is booked, trading is locked until arrival
   - Missed opportunities are intentional, not accidental

3. **The World Reacts, It Never Explains**
   - Multiplayer effects are discovered slowly
   - No UI labels for “other players”
   - No explicit explanations of cause

---

## Starting Conditions (LOCKED DEFAULTS)

- Starting Cash: **$20,000**
- Starting Debt: **$30,000**
- Inventory Capacity: **100 units**
- Debt Interest: **~0.8% per real-world hour (compounding)**
- Debt exists immediately at game start

The player begins **already under pressure**.

---

## Debt & Loan Shark Rules

- The player starts with mandatory debt
- Debt accrues interest in real time, even while offline
- Debt can ONLY be paid, reduced, or renegotiated in the **city of origin**
- The loan shark is permanently tied to the starting city
- Ignoring debt causes gradual escalation:
  - Higher interest
  - Increased enforcement pressure
  - Reduced effectiveness of bribes, fixers, and safehouses
- Failure is gradual escalation, not instant loss

Debt creates a **gravitational pull** back to the origin city.

---

## Travel System Rules

- Travel uses static/open data only (airports, distance, heuristics)
- Flight duration is calculated, not looked up live
- No fast travel
- No skipping time

Travel Classes:
- Economy: cheapest, slowest, highest scrutiny
- Business: balanced, reduced risk
- First: expensive, fastest, lowest scrutiny, limited special actions

Once travel begins:
- Trading is disabled
- Prices continue to update
- Market visuals continue to animate

---

## Market & Pricing Rules

- Prices are **explicit and numeric**
- Prices are lowest near manufacturing regions
- Prices rise with:
  - Distance from source
  - Enforcement pressure
  - Scarcity
  - Aggregate player activity

Prices may spike or crash dramatically.

---

## Market Visualization Rules

UI must show:
- Current price (always visible)
- Percent change (simple ▲ / ▼)
- A **visual market signal** (e.g. volatility ribbon / pulse)

UI must NOT show:
- Candlestick charts
- OHLC data
- Exact historical tables
- Technical indicators (RSI, MACD, etc.)

Visuals should convey:
- Momentum
- Volatility
- Liquidity
- Instability

The goal is intuition, not analysis paralysis.

---

## Inventory Rules

Inventory is physical:
- Volume limits apply
- Bulk increases risk and friction
- Optional decay/spoilage over time
- Storage limits vary by city
- Safehouses reduce loss and exposure

No infinite hoarding.

---

## Law Enforcement Model

- ~180 countries
- One national enforcement org per country (fictionalized names)
- Attributes include:
  - Aggression
  - Reach
  - Efficiency
  - Corruption
  - International cooperation

Heat is:
- Country-specific
- Transferable across borders
- Influenced by volume, time exposed, and transport method

Players never fight law enforcement directly.
Pressure is environmental.

---

## Multiplayer Philosophy (CRITICAL)

- Multiplayer is **asynchronous and indirect**
- Players never see:
  - Other players
  - Player names
  - Player locations
  - Player inventories

Players influence the world only through:
- Aggregate demand
- Market volatility
- Enforcement pressure

Discovery of multiplayer effects must be **gradual and implicit**.

The world never says “another player did this”.

---

## Code Organization Rules

- Backend logic must be deterministic
- UI must not contain business logic
- Each system lives in its own file
- Avoid monolithic “god files”

Preferred structure:
- backend/ → world logic
- frontend/ → UI only
- data/ → static datasets
- docs/ → rules and explanations

---

## AI Agent Expectations

When coding:
- Prefer clarity over cleverness
- Explain *why* in comments, not *what*
- Never introduce paid services
- Never assume real-time multiplayer visibility
- Ask before adding complexity

When uncertain:
- Default to simpler mechanics that preserve tension
- Preserve consequences over convenience

---

## Design North Star

If a feature:
- Reduces planning
- Removes commitment
- Eliminates risk
- Explains the system too clearly

…it probably does not belong.

The game should feel like:

**“The world keeps moving, and I’m already behind.”**
