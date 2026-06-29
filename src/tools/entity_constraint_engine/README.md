# Entity Constraint Engine

## Overview
**What it does:** It acts as the internal database reader for the Constraint Agent. It is completely isolated per entity to ensure rules don't bleed across rooms.

**How it works internally:**
1.  When asked for rules regarding a `"bedroom"`, it connects to `database.db`.
2.  It queries `EntitySpecs` to build `size_rules` (min areas, aspect ratios) and `feature_rules` (egress, windows, doors).
3.  It then queries `RelationalRules` to find any adjacency or distance constraint where the `"bedroom"` is involved (either as Entity A or Entity B).
4.  It packages this into a modular dictionary and returns it to the Constraint Agent.

## Testing the Entity Constraint Engine

To debug or query the raw baseline rules for a specific entity type (e.g. what are the default rules for a bedroom?), run the engine directly. You can pass multiple entities separated by spaces, or pass `all` to output everything. The outputs are automatically saved to the `Entity_Constraints` folder.

*(Currently available entities: `bedroom`, `bathroom`, `kitchen`, `living`, `dining`, `corridor`, `laundry`, `garage`, `balcony`)*

**For a specific room:**
```bash
python3 entity_constraint_engine.py bedroom
```
*(Generates `Entity_Constraints/bedroom.json`)*

**For multiple specific rooms:**
```bash
python3 entity_constraint_engine.py bedroom bathroom kitchen
```
*(Generates `Entity_Constraints/bedroom_bathroom_kitchen.json`)*

**For all rooms at once:**
```bash
python3 entity_constraint_engine.py all
```
*(Generates `Entity_Constraints/all_entities.json`)*
