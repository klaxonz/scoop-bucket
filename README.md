# klaxonz Scoop bucket

Personal [Scoop](https://scoop.sh) bucket for apps that no official bucket ships yet.
Manifests are kept current by the Excavator workflow (every 4 hours).

## Usage

```powershell
scoop bucket add klaxonz https://github.com/klaxonz/scoop-bucket
scoop install klaxonz/<app>
```

## Manifests

| App | Version source | Notes |
| --- | --- | --- |
| `mygo-music` | [egoist/mygo-music](https://github.com/egoist/mygo-music) | Native Go/MyGo music player. Not in `extras`, `apps`, `lemon`, `dorado` or winget. NSIS installer repacked via `#/dl.7z`; `$PLUGINSDIR` and `Uninstall.exe` stripped in `pre_install`. |

Candidates for a manifest here: apps whose upstream ships only an NSIS installer or a
PowerShell one-liner, and that no other bucket covers.

## Adding a manifest

Copy `bucket/app-name.json.template`, fill it in, then validate locally:

```powershell
.\bin\checkver.ps1 -App <app>
.\bin\checkver.ps1 -App <app> -u      # exercises autoupdate + hash computation
.\bin\checkhashes.ps1 -App <app> -Update
```

Commit and push; CI (Pester lint) runs on `main`.

## License

[MIT](LICENSE)
