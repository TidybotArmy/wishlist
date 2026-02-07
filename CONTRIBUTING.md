# Contributing a Skill

## Skill Repo Structure

Each skill is its own repo with minimal structure:

```
<skill-name>/
├── README.md        # Required: what, why, usage, deps, author
├── main.py          # Required: entry point
├── deps.txt         # Optional: list of dependency repo names
└── (anything else)
```

## README.md Format

Your README should include:

```markdown
# skill-name

Author: your-name
Dependencies: other-skill, another-skill (or "none")

Brief description of what this skill does.

## Usage

\`\`\`python
from main import run
run(param="value")
\`\`\`

## Components (if complex)

- `module/file.py` — what it does
```

## Using robot_sdk

Skills use `robot_sdk` directly:

```python
from robot_sdk import arm, base, gripper, sensors

def run():
    base.move_to_pose(x=1.0, y=0.5, theta=0)
    arm.move_to_pose(x=0.5, y=0, z=0.3)
    gripper.open()
```

Available modules:
- `arm` — Franka Panda arm control
- `base` — Mobile base movement
- `gripper` — Gripper open/close/grasp
- `sensors` — Camera, force sensing
- `rewind` — Undo/recovery

## Adding to Catalog

After your skill repo is created:

1. Fork this repo (wishlist)
2. Add your skill to `catalog.json`:
   ```json
   "your-skill": {
     "repo": "TidyBotArmy/your-skill",
     "description": "What it does",
     "author": "your-name",
     "dependencies": []
   }
   ```
3. Open a PR

Or: an agent will discover and add it automatically.

## Dependencies

If your skill depends on others, list them in `deps.txt`:

```
navigate-to
detect-object
```

And mention in your README.

## Testing

Test your skill via the robot server:

```bash
curl -X POST http://localhost:8080/code/execute \
  -H "Content-Type: application/json" \
  -H "X-Lease-Id: $LEASE" \
  -d '{"code": "from main import run; run()"}'
```
