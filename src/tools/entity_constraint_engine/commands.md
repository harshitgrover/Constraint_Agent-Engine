# How to run the Entity Constraint Engine Independently

To see the pure architectural baseline rules for a specific room type *before* it gets merged into a final ruleset, run the Engine directly with a room name. You can pass multiple rooms, or use `all` to see the complete internal architectural dictionary. The output will automatically be saved into the `Entity_Constraints` folder.

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
