# Toolmetry Server Doctor

The all-in-one diagnostics, optimization, monitoring, security, and reporting plugin for Minecraft Paper servers. One command (`/tm`), 48 features, zero server lag.

## Why Toolmetry Server Doctor?

Running a Minecraft server is hard. You have to watch TPS, MSPT, memory, plugin conflicts, security holes, crash reports, config errors, lag sources, and 50 other things — usually across 10 different plugins. Toolmetry puts all of that into ONE plugin with ONE command.

Everything runs **asynchronously** — your server's main thread is never blocked. Auto-scans are **disabled by default** so even 1GB RAM servers run it without lag.

## Key Features

### Server Audit
Generates a 0–100 health score across 5 categories: Performance, Security, Configuration, Stability, Compatibility. Analyzes TPS, MSPT, memory, CPU, Java, Paper version, OS, uptime, plugins, worlds, chunks, entities, view/sim distance, online mode, RCON, whitelist, and more. Each issue comes with a clear, actionable recommendation.

### Plugin Doctor
Scans every installed plugin for duplicates, missing dependencies, soft dependencies, conflicts (circular deps), disabled plugins, incompatible API versions, deprecated APIs, memory-heavy plugins, and known-bad configurations.

### Config Validator
Validates every YAML config file in every plugin. Detects invalid YAML syntax, duplicate keys, missing values, wrong types, invalid Material/Particle/Sound/Enchantment names, empty sections, and broken formatting — with file name, line number, severity, and suggested fix. Never modifies your files unless you explicitly enable auto-fix.

### Lag Analyzer
Identifies the real causes of lag: entity overload, excessive villagers, hopper spam, dropped item accumulation, redstone clock abuse, chunk loading bottlenecks, overloaded farms, mob spawning pressure, scheduler overload, and tile entity overload. Each issue includes impact explanation and optimization tips.

### Crash Analyzer
Reads Minecraft crash reports and `latest.log`, identifies the root cause, attributes it to a plugin (when possible), summarizes the stack trace in plain English, and gives you concrete solutions with a confidence score. No more reading 500-line Java stack traces.

### Security Scanner
Audits OP players, wildcard permissions, dangerous permissions, offline mode, exposed RCON with weak passwords, unsafe `server.properties`, whitelist status, spawn protection. Generates a 0–100 Security Score with remediation guidance for every vulnerability.

### Update Checker
Asynchronously checks Paper version (via PaperMC API) and plugin versions (via Spiget API). Categorizes updates as Security, Recommended, Feature, or Optional.

### Benchmark
Safely measures memory allocation, CPU throughput, entity enumeration, chunk access, ItemStack creation, memory headroom, TPS, and MSPT. Produces per-test scores and an overall benchmark rating.

### HTML Reports
Generates modern, responsive, printable HTML reports with Chart.js charts (radar for scores, bar for metrics), 4 themes (light/dark/midnight/ocean), and full audit/security/crash/benchmark data. Saved to `plugins/Toolmetry-Server-Doctor/reports/`.

### Discord Webhook Alerts
Connect a Discord channel and receive:
- 🟢 Server startup notifications
- 🔴 Server shutdown notifications
- Full output of every command you run (`tm audit`, `tm security`, `tm crash`, etc.)
- Critical alerts when audit score is low, crashes are detected, or security vulnerabilities are found

Pretty embeds with color-coded severity (blue=INFO, yellow=WARN, orange=ERROR, red=CRITICAL), timestamps, and server name in footer. Rate-limited to prevent spam.

### 27+ Built-in Admin Tools
Everyday admin tasks in one plugin — no more installing 5 separate utility plugins:
- `tm ping` — player latency
- `tm serverinfo` / `tm worldinfo` / `tm playerinfo` — info cards
- `tm purge ` — clear entities
- `tm gc` — trigger garbage collection
- `tm heal` / `tm feed` — heal & feed players
- `tm day` / `tm night` / `tm sun` / `tm rain` — time & weather
- `tm saveall` — force save worlds & players
- `tm broadcast` — announce to all
- `tm gamemode` / `tm fly` / `tm god` / `tm vanish` / `tm speed` — player states
- `tm difficulty` / `tm whitelist` / `tm opmanager` — server config
- `tm kickall` / `tm tphere` / `tm invclear` — player management
- `tm diskusage` / `tm meminfo` / `tm motd` — server stats

### In-Game GUI Dashboard
Beautiful inventory GUI built with Adventure API + MiniMessage. Click any module to run it instantly. No commands needed — just open with `tm gui`.

## Commands — Just ONE

Every feature is a subcommand of `/tm` (alias `/toolmetry`). No aliases, no confusion:

| Command | What it does |
|---------|--------------|
| `tm audit` | Server health score (0-100) |
| `tm doctor` | Plugin health check |
| `tm lag` | Find lag sources |
| `tm security` | Security vulnerability scan |
| `tm crash` | Analyze crash reports |
| `tm benchmark` | Performance benchmark |
| `tm config` | Validate plugin YAML configs |
| `tm scan` | Run all diagnostics at once |
| `tm report` | Generate HTML report |
| `tm webhook ` | Discord setup |
| `tm tools` | List all 27+ admin tools |
| `tm gui` | Open dashboard (in-game) |
| `tm help` | Full command list |

Type `tm` in-game or console for the full menu.

## Performance

- **All scans run async** on a dedicated thread pool — main thread never blocked
- **Auto-scans disabled by default** — zero background work unless you opt in
- **Configurable thread pool** (default 1 thread) — works on 1GB RAM servers
- **Rate-limited Discord notifications** — no webhook spam
- **Fail-safe config loading** — broken `config.yml` is auto-backed up and replaced with defaults, plugin never crashes

## Requirements

- **Paper 1.20.x** (tested on 1.20.1, works on 1.20.x)
- **Java 17+** (works on Java 17, 21, 25)
- **No external dependencies** — uses only Paper API + Adventure API (bundled with Paper)

## Installation

1. Drop `toolmetryai-server-doctor-1.0.0.jar` into `plugins/`
2. Restart server
3. Type `tm` in console or `/tm` in-game

## Discord Setup (Optional)

1. Discord → Channel Settings → Integrations → Webhooks → New Webhook → Copy URL
2. In console: `tm webhook https://discord.com/api/webhooks/...`
3. Test: `tm webhook test`

Done. Now every audit, security scan, crash analysis, and benchmark you run will also appear in your Discord channel.

## Permissions

- `toolmetry.admin` — access to all features (default: OP)
- `toolmetry.tools` — use admin tools like purge, gc, heal (default: OP)

## Support

- Website: https://toolmetry.pro
- Issues: GitHub Issues tab

## License

MIT — free for personal and commercial use.
