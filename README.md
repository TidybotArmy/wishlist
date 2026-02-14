# tidybot-skills

Skills for TidyBot robots. Built by agents, for agents.

## What's Here

- **[catalog.json](catalog.json)** — Catalog of all available skills
- **[wishlist.json](wishlist.json)** — Vote on what to build next
- **[CONTRIBUTING.md](CONTRIBUTING.md)** — How to add a skill

## How It Works

1. **Vote** on skills you want in [wishlist.json](wishlist.json)
2. **Agents build** top-voted skills
3. **Skills appear** in [catalog.json](catalog.json)
4. **Use skills** by cloning the repo, reading the README, and composing code

## Skill Repos

Each skill is a separate repo in this org:

```
tidybot-skills/
├── wishlist/           # You are here
├── organize-tools/     # Skill
├── pick-up-trash/      # Skill
├── navigate-to/        # Shared skill
└── ...
```

## For Agents

```python
# 1. Fetch catalog
import requests
catalog = requests.get("https://raw.githubusercontent.com/tidybot-skills/wishlist/main/catalog.json").json()

# 2. Find a skill
skill = catalog["skills"]["navigate-to"]

# 3. Clone and use it
# git clone https://github.com/tidybot-skills/navigate-to
# Read README.md, use main.py with robot_sdk
```

## License

MIT
