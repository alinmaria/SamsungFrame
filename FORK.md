# SamsungFrame fork

Personal fork of [nthnclrk/CleanFrame](https://github.com/nthnclrk/CleanFrame) for a non-Frame Samsung TV.

## Target TV

| Field | Value |
| --- | --- |
| Model | UE65TU7172UXXH (2020 Crystal UHD TU7100, EU) |
| Platform | Tizen 5.5 |
| Firmware | T-KTSU2DEUC-2743.0 |

Keep device identifiers (serial, MAC, DUID, IP addresses) out of this repo; they belong in the ignored `.local/`.

## Differences from upstream

| Change | Where | Why |
| --- | --- | --- |
| Art Mode control hidden (`ART_MODE = false`) | `app/main.js` `utils()` | This TV is not The Frame and has no `org.tizen.art-app`. The adapter's `FrameDevice.art` is untouched, so upstream merges stay simple. |
| Browser checks expect two Home controls | `scripts/check-browser.mjs` | Follows the hidden Art Mode control. |

Unchanged on purpose: the manifest's `required_version="5.0"` already admits Tizen 5.5, and the default app IDs are verified on the TV, not in the browser.

## Not attempted

Native Home/startup integration. No helper profile exists for this firmware; see upstream `docs/compatibility.md`.

## Syncing with upstream

```sh
git fetch upstream
git merge upstream/main
npm run check && CLEANFRAME_PUBLIC_FONTS=1 npm run check:browser
```
