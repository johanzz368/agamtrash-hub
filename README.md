# agamtrash-hub

`agamtrash.hub` — authorized Roblox development hub bundle.

`agamtrash-hub.lua` is **one dual-mode file** containing all runtime code:

- 16 shared modules
- 13 client modules (Rayfield interface)
- 9 server modules (authorization, remotes, fixtures)
- the reviewed vendored Rayfield source

The same file chooses its branch automatically:

- executed by an executor or a `LocalScript` -> client/Rayfield branch;
- executed by a `Script` in `ServerScriptService` -> server component branch.

## Run the client

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/johanzz368/agamtrash-hub/main/agamtrash-hub.lua"))()
```

Running it only in an executor starts the client branch. The server component is
absent there, so gameplay features stay locked by design — this is not a UI bug.

## Run the full hub in a place you own

1. Paste the same `agamtrash-hub.lua` into a `Script` in `ServerScriptService`.
2. Paste it again into a `LocalScript` in `StarterPlayerScripts`.
3. In the embedded `ServerConfig` block, set `AllowStudio`, your
   `AuthorizedPlaceIds` and `TesterUserIds`.

Only use this in an experience you own or are explicitly authorized to modify.
The project has no integration with, remotes for, or bypasses for a third-party
game. Rayfield is Apache-2.0; see the upstream project for its license.