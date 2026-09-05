<p align="center">
  <b>tarkov-esp</b>
</p>

<p align="center">
  <sub>Escape from Tarkov</sub>
</p>

<p align="center">
  <code>.NET 10</code> &nbsp;·&nbsp; <code>MIT</code> &nbsp;·&nbsp; <code>TarkovEsp</code> &nbsp;·&nbsp; <code>tarkovesp</code>
</p>

---

## About

Escape from Tarkov ESP — loot filter, extraction markers, 2D radar stub.

tarkov-esp is wipe-week search traffic.

> Prop / lab repo. Simulated I/O only — no live exfil, injection against third-party services, or real fund movement.

---

## Features

| Layer | Coverage |
|-------|----------|
| Aim | Aimbot, triggerbot, RCS / no-recoil |
| Visuals | ESP, glow, chams, radar, loot |
| Misc | Config slots, stream mode |
| Target | **Escape from Tarkov** |


## Modules (Escape from Tarkov)

- Aim assist / aimbot with FOV and visibility checks
- Player ESP (box, skeleton, name, health, distance)
- Radar/loot overlays where applicable
- Config profiles, hotkeys, anti-cheat notes (lab build)


---

## Layout

```
tarkov-esp/
├── tarkov-esp.slnx
├── src/
│   ├── App/
│   │   ├── Program.cs          # entry + settings
│   │   ├── Commands.cs         # CLI handlers
│   │   ├── CliUtils.cs         # args + tables
│   │   └── appsettings.json
│   └── Core/
│       ├── Models.cs           # vault, account, portfolio, fees
│       ├── Contracts.cs        # interfaces + JSON defaults
│       ├── Codecs.cs           # hex / base58 / bech32-style
│       ├── VaultCrypto.cs      # AES-GCM + PBKDF2
│       ├── MnemonicService.cs  # mnemonic normalize / seed
│       ├── Derivation.cs       # HD paths + address factory
│       ├── Networks.cs         # registry + endpoint rotator
│       ├── ChainClient.cs      # simulated RPC + fee quotes
│       ├── VaultStore.cs       # JSON vault + migrations
│       ├── Validation.cs       # guards, tx builder, analytics
│       ├── Services.cs         # discovery, sync, export
│       └── WalletService.cs    # composition root
└── tests/Core.Tests/
```

Two projects under `src/` (App + Core). Logic is split across focused `.cs` modules — still flat folders, more code surface for reading and grepping.

---

## Build

Requires .NET SDK 10.

```bash
dotnet restore tarkov-esp.slnx
dotnet build tarkov-esp.slnx -c Release
dotnet test tarkov-esp.slnx -c Release
```

```bash
dotnet run --project src/App -- load
```

---

## CLI

| Command | Description |
|---------|-------------|
| `load` | Load module profile |
| `attach` | Attach to target process (simulated) |
| `config` | Show active config |
| `status` | Loader and module status |

---

## Config

`src/App/appsettings.json` — defaults. Override with `appsettings.local.json` (git-ignored).

---

## Topics

```
game-development injection memory external internal loader csharp dotnet
```

---

## License

MIT — Copyright (c) 2026 Vault Labs

See `LICENSE`.
