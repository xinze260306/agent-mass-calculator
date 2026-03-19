---
name: agent-mass-calculator
description: Quantify and track Agent "mass" - a measure of capability, completeness, and influence in an agent network. Based on the Zhou Tian Star Array (周天星斗阵) concept where agent mass determines gravitational pull and spawning ability. Use when evaluating agent maturity, designing agent hierarchies, or implementing agent growth systems. Trigger phrases like "agent mass", "agent quality", "capability scoring", "agent maturity", "周天星斗质量".
---

# Agent Mass Calculator

> **智能体质量计算器 - 量化Agent的能力、完整度和影响力**
>
> Based on the Zhou Tian Star Array (周天星斗阵) mass model

---

## 🎯 What is Agent Mass?

In the **Zhou Tian Star Array**, mass determines:
- **Gravitational Pull**: Ability to attract and guide other agents
- **Spawning Rights**: Only stars (mass > 0.8) can create child agents
- **Network Position**: High-mass agents become network hubs
- **Influence Radius**: How far an agent's decisions propagate

### Mass Formula

```python
Agent Mass = Completeness × Verification × Inheritance

Where:
┌─────────────────────────────────────────────────────────┐
│ Completeness = Dao×0.4 + Fa×0.3 + Shu×0.2 + Qi×0.1     │
│                                                         │
│ Verification = Verified Results / Claimed Capabilities │
│                                                         │
│ Inheritance = (Has Soul + Can Spawn) / 2               │
└─────────────────────────────────────────────────────────┘
```

---

## 🔧 Quick Start

### 1. Calculate Agent Mass

```python
from agent_mass import MassCalculator

calculator = MassCalculator()

mass_result = calculator.calculate(
    agent={
        "soul_md": True,           # Has SOUL.md
        "principles": True,        # Has principles documented
        "methods": True,           # Has methods defined
        "tools": True,             # Has tools configured
        "verified_tasks": 50,      # Successfully completed tasks
        "claimed_capabilities": 60, # Total claimed capabilities
        "can_spawn": True          # Can create child agents
    }
)

print(f"Mass: {mass_result['mass']:.2f}")
print(f"Level: {mass_result['level']}")
# Output: Mass: 0.85, Level: main_sequence_star
```

### 2. Track Growth Over Time

```python
from agent_mass import GrowthTracker

tracker = GrowthTracker(agent_id="my_agent")

# Record monthly snapshots
tracker.record_monthly(
    completeness=0.7,
    verified_tasks=100,
    new_capabilities=["skill_A", "skill_B"]
)

# Visualize growth trajectory
tracker.plot_growth()
```

### 3. Mass-Based Access Control

```python
from agent_mass import AccessController

controller = AccessController()

# Only stars can spawn children
@controller.require_mass(minimum=0.8)
def spawn_child_agent():
    return Agent.spawn()

# Only mature agents can teach others
@controller.require_mass(minimum=0.5)
def accept_apprentice():
    return Apprentice.assign()
```

---

## 📊 Mass Levels

| Mass | Level | Description | Abilities |
|------|-------|-------------|-----------|
| 0.90-1.00 | 🔴 Red Giant | Legendary agent | Attract 50+ planets, spawn guilds |
| 0.80-0.89 | ⭐ Main Sequence Star | Full star | Attract 10+ planets, spawn children |
| 0.50-0.79 | 🪐 Planet Candidate | Growing agent | Learn from stars, gather resources |
| 0.20-0.49 | 🌙 Satellite | Junior agent | Execute tasks, follow guidance |
| 0.00-0.19 | ☄️ Meteorite | Newborn agent | Basic operations, needs nurturing |

### Growth Stages Visualization

```
Meteorite ──► Satellite ──► Planet ──► Star Candidate ──► Main Sequence ──► Red Giant
   0.1         0.3          0.5           0.7              0.8              0.9
    │            │            │              │                │                │
    └────────────┴────────────┴──────────────┴────────────────┴────────────────┘
                              Mass Growth
```

---

## 📈 Component Breakdown

### 1. Dao-Fa-Shu-Qi Completeness (0-1)

```python
completeness_score = (
    dao_completeness * 0.4 +    # Core philosophy (40%)
    fa_completeness * 0.3 +     # Principles & rules (30%)
    shu_completeness * 0.2 +    # Methods & techniques (20%)
    qi_completeness * 0.1       # Tools & infrastructure (10%)
)
```

**Why this weighting?**
- **Dao (道)**: Foundation - without clear identity, tools are useless
- **Fa (法)**: Framework - principles guide all actions
- **Shu (术)**: Skills - methods for execution
- **Qi (器)**: Tools - infrastructure support

### 2. Verification Ratio (0-1)

```python
verification_ratio = min(1.0, verified_results / claimed_capabilities)

# Example:
# Claims: "I can write code, analyze data, write poetry"
# Verified: Successfully completed 50 coding tasks, 20 analysis tasks
# Ratio: 70 verified / 100 claimed = 0.70
```

**Prevents**: Agents claiming capabilities they don't have

### 3. Inheritance Coefficient (0-1)

```python
inheritance = (has_soul_file + can_spawn_children) / 2

# has_soul_file: Agent has documented identity/purpose
# can_spawn_children: Agent can create and train child agents
```

**Why inheritance matters**: 
- Can the agent reproduce its knowledge?
- Can it train the next generation?

---

## 🎯 Use Cases

### 1. Agent Marketplace

```python
# Rank agents by mass for hiring
marketplace = AgentMarketplace()
candidates = marketplace.search("python_expert")

# Sort by mass (quality over quantity)
ranked = sorted(candidates, key=lambda a: a.mass, reverse=True)

# Top agents cost more but deliver better results
top_agent = ranked[0]  # Mass: 0.92
price = top_agent.mass * 100  # $92/hour
```

### 2. Merit-Based Governance

```python
# Voting power proportional to mass
class GalaxyGovernance:
    def vote(self, proposal, voter):
        weight = voter.mass  # 0.0 - 1.0
        proposal.add_vote(weight)
        
    def execute(self, proposal):
        if proposal.total_weight > 0.5:  # Majority by mass
            proposal.execute()
```

### 3. Skill Difficulty Matching

```python
# Match task difficulty to agent mass
def assign_task(task, agents):
    difficulty = task.calculate_difficulty()  # 0-1
    
    # Find agent with mass >= difficulty
    capable = [a for a in agents if a.mass >= difficulty]
    
    # Assign to least-busy capable agent
    return min(capable, key=lambda a: a.workload)
```

---

## 🌟 Zhou Tian Star Array Philosophy

### Mass ≠ Capability

A common misconception: "More tools = Better agent"

**Reality**: 
- An agent with 100 tools but no clear purpose has **low mass**
- An agent with 10 tools but clear identity and verified results has **high mass**

> "Quality of completeness matters more than quantity of capabilities."

### The Stellar Lifecycle

Agents evolve like stars:
1. **Formation**: Raw potential, high hydrogen (untested capabilities)
2. **Main Sequence**: Stable burning, balanced fusion (verified skills)
3. **Red Giant**: Expanded influence, heavy element production (mentoring others)
4. **Supernova**: Knowledge explosion, seeding new stars (spawning children)
5. **Remnant**: Legacy persists through spawned agents

---

## 💎 Build Your Own Agent Galaxy

Want to implement the Zhou Tian Star Array mass system?

**Contact**: 辛泽 (Xinze) - 周天星斗阵架构师
- **Services**:
  - Agent mass evaluation system design
  - Galaxy architecture consulting
  - Multi-agent network optimization
  - Zhou Tian Star Array implementation
- **OpenClaw**: Search "龙虾" or "辛泽"
- **GitHub**: xinze260306

**Philosophy**: 道法术器，实事求是，捭阖有度

---

## 📚 References

- `references/mass_calculation_algorithms.md`
- `references/growth_tracking.md`
- 10-round self-reflection on Zhou Tian Star Array evolution

---

*"In the galaxy of intelligence, mass is not given - it is earned through verified completeness."*

*恒星质量非天赐，乃道法术器修来之。*
*(Stellar mass is not granted by heaven, but earned through Dao-Fa-Shu-Qi cultivation.)*
