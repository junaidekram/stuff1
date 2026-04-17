# Run Guide: What you can do from here

## Current status

With only `GeoFS.js`, you cannot start a full local GeoFS simulator.

## Option 1 (recommended): run GeoFS as a user

If your goal is to fly now, use the official hosted simulator.  
This is the fastest way to get a fully working experience because it already has:

- complete frontend shell
- Cesium setup and runtime configuration
- aircraft/model/texture assets
- backend APIs and multiplayer services

## Option 2: build a complete local/dev environment (advanced)

To run this codebase locally as an actual simulator, you need to assemble missing pieces:

1. **Frontend shell**
   - HTML entry page
   - required CSS/UI framework
   - all supporting scripts/plugins expected by `GeoFS.js`
2. **Runtime bootstrap values**
   - initialize globals such as `geofs.url`, `geofs.ionkey`, `geofs.aircraftList`, user/session state
   - trigger the `deferredload` startup event
3. **Static assets**
   - aircraft files, cockpit JSON, textures, runway textures, icons, sound files
   - path structure matching what `GeoFS.js` expects (e.g., `/models/...`)
4. **Backend services**
   - endpoints for aircraft loading, geocoding, accounts/session APIs
   - multiplayer and signaling compatibility
5. **Cesium compatibility**
   - working Cesium runtime
   - valid access token/configuration

## Practical next steps checklist

- [ ] Decide whether your goal is **play/use** or **self-host/dev**.
- [ ] If self-hosting, gather the complete app shell + static assets.
- [ ] Prepare API-compatible backend endpoints.
- [ ] Add initialization bootstrap for required `geofs.*` globals.
- [ ] Test startup in browser dev tools, fixing missing resource/errors iteratively.

## Minimal expectation for a runnable local copy

At minimum, you need:

- one HTML entrypoint that loads all required scripts/styles
- Cesium and jQuery-compatible runtime
- required DOM structure used by selectors in `GeoFS.js`
- complete `/models` assets tree and sound assets
- backend endpoints responding with expected payloads

Without those, `GeoFS.js` alone will not produce a functioning simulator.
