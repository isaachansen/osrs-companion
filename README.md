# osrs-companion

An MCP server for Old School RuneScape that gives AI assistants access to
wiki search, Grand Exchange prices, and your synced player data — all running
locally on your machine.

## Features

- **Wiki Search** — Search the OSRS Wiki for any article
- **Page Summaries** — Get introductory summaries of wiki pages
- **GE Prices** — Look up current Grand Exchange buy/sell prices
- **WikiSync Player Data** — Fetch player data via the WikiSync plugin
- **Local Player Sync** — Read detailed player data saved by the companion RuneLite plugin (bank, skills, quests, equipment, inventory, diaries, combat achievements)

## Prerequisites

For the local player sync tools, install the **OSRS MCP Companion** RuneLite
plugin. Wiki search, summaries, and GE prices work without it.

## Installation

### Claude Code / Claude Desktop

Add to your MCP configuration:

```json
{
  "mcpServers": {
    "osrs-companion": {
      "command": "npx",
      "args": ["-y", "osrs-companion"]
    }
  }
}
```

### Manual

```bash
npx -y osrs-companion
```

## Available Tools

### Wiki Tools
| Tool | Description |
|------|-------------|
| `search` | Search the OSRS Wiki for articles |
| `summary` | Get the intro summary of a wiki page |
| `price` | Look up Grand Exchange prices |
| `player` | Fetch player data via WikiSync |

### Player Sync Tools (requires RuneLite plugin)
| Tool | Description |
|------|-------------|
| `list_synced_players` | List players with synced data |
| `get_my_profile` | Full player summary |
| `get_my_bank` | Search bank contents |
| `get_my_stats` | Skill levels and XP |
| `get_my_quests` | Quest completion status |
| `get_my_equipment` | Currently equipped items |
| `get_my_inventory` | Current inventory |
| `get_my_diaries` | Achievement diary progress |
| `get_my_combat_achievements` | Combat achievement status |

## How It Works

The MCP server runs locally via stdio transport. Wiki and price tools
fetch from public OSRS APIs. Player sync tools read JSON files from
`~/.runelite/mcp-sync/` that are written by the companion RuneLite plugin.

No data is stored in the cloud. No API keys required.

## License

BSD 2-Clause "Simplified" License. See [LICENSE](LICENSE).
