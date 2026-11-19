# Volkyport-New

Port source for [Volkyport](https://github.com/Volkybaba/PortMaster-GUI)
(the Volkyport GUI, a fork of PortMaster-GUI).

The GUI fetches its port list from the latest release here:

    https://github.com/Volkybaba/Volkyport-New/releases/latest/download/ports.json

## How it works

- Each release holds the port zips as assets plus a `ports.json` asset.
- `ports.json` has two top-level keys: `ports` (one entry per port zip,
  keyed by zip filename, with `source.md5`, `source.size` and `source.url`
  pointing at the release asset) and `utils` (`gameinfo.zip`, `images.zip`).
- Port zips are flat: the launcher `.sh`, `port.json`, `gameinfo.xml`,
  `README.md` and the game folder at the zip root. No game data is
  included; the player supplies their own legally owned game files.
- `port.json` `version` is the PortMaster schema version (currently 4),
  never the package version.

## Adding a port

1. Build the flat zip from the port folder (`~/workspace/portmaster/<port>`).
2. Upload the zip as an asset of a new release (tag `YYYY-MM-DD_HHMM`).
3. Add its entry to `ports.json` (copy an existing entry, update `md5`,
   `size`, `release_id` and `url`), upload `ports.json` to the same release.
4. If the port has a cover/screenshot, add `<port>.cover.png` /
   `<port>.screenshot.png` to `images.zip` and its `gameinfo.xml` to
   `gameinfo.zip` (as `<port>/gameinfo.xml`), and re-upload both utils.
