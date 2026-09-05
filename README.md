<p align="center">
  <b>valorant-external</b>
</p>

<p align="center">
  <sub>Valorant</sub>
</p>

<p align="center">
  <code>.NET 10</code> &nbsp;·&nbsp; <code>MIT</code> &nbsp;·&nbsp; <code>ValExt</code> &nbsp;·&nbsp; <code>valext</code>
</p>

---

## About

Valorant external overlay — player ESP, stream-proof toggle, config profiles.

External and internal split matches how buyers actually search.

> Prop / lab repo. Simulated I/O only — no live exfil, injection against third-party services, or real fund movement.

---

## Features

| Layer | Coverage |
|-------|----------|
| Aim | Aimbot, triggerbot, RCS / no-recoil |
| Visuals | ESP, glow, chams, radar, loot |
| Misc | Config slots, stream mode |
| Target | **Valorant** |


## Modules (Valorant)

- Aimbot smooth/FOV, triggerbot, player + spike ESP
- Trap/gadget ESP, stream-proof overlay, Vanguard notes (lab attach only)


---

## Layout

```
valorant-external/
├── valorant-external.slnx
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
dotnet restore valorant-external.slnx
dotnet build valorant-external.slnx -c Release
dotnet test valorant-external.slnx -c Release
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
