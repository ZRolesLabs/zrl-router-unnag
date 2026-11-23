<p align="center"><img src="icons/icon128.png" width="96" alt="ZRL Cloud-Nag Suppressor icon"></p>

<h1 align="center">ZRL Cloud-Nag Suppressor</h1>
<p align="center"><b>Make the TP-Link cloud login popup go away on your Archer router's admin page.</b><br>
A ZRoles Labs project. CSS only. No scripts, no permissions, no network.</p>

---

## The problem

Log in to a TP-Link Archer router locally and you get a popup pushing you to bind the router to a
**TP-Link ID / cloud account**. Dismiss it and it comes back on the next login. If you run your
network local-only on purpose, it is just in the way, and on some firmware the dark overlay behind it
blocks clicks on the page.

## What this does

It is a tiny browser extension that adds one stylesheet to your router's admin page. That stylesheet
hides the cloud popup and its overlay. That is all.

- **No JavaScript.** The extension is `manifest.json` + `unnag.css` + icons. Read both files in a minute.
- **No permissions.** Chrome shows no permission prompt when you load it.
- **No network.** It never talks to anything. It cannot see or change your router settings.
- **Only your router pages.** It runs only on `tplinkwifi.net`, `192.168.0.1` and `192.168.1.1`.
- **Other dialogs still work.** Only the cloud popup and its own overlay are hidden.

It does **not** change anything on the router. The cloud feature is still there in the router's menus
if you ever want it.

## Works with

| Router | Firmware | Status |
|---|---|---|
| Archer GXE75 | 1.0.5 | ✅ tested |
| Archer GXE75 | 1.1.4 | ✅ tested |
| Other Archer models | any | 🤷 likely, since TP-Link reuses the same web UI. Please report! |

Browsers: Chrome, Edge, Brave, and other Chromium browsers.

## Install (about one minute)

1. Download this repository: click the green **Code** button, then **Download ZIP**, or grab the zip
   from **Releases** on the right. Unzip it somewhere it can stay (the browser loads it from that folder).
2. In your browser, open the extensions page: `chrome://extensions` (Edge: `edge://extensions`, Brave: `brave://extensions`).
3. Turn on **Developer mode** (top right in Chrome, left side in Edge).
4. Click **Load unpacked** and pick the unzipped folder (the one that contains `manifest.json`).
5. Log in to your router. No popup. 🎉

To update later: replace the folder contents with the new version, then click the circular-arrow
**reload** icon on the extension's card.

## My router uses a different address

If you reach your router at something other than `tplinkwifi.net`, `192.168.0.1` or `192.168.1.1`
(for example `10.0.0.1`), open `manifest.json` in a text editor and add two lines to the `matches`
list:

```json
"http://10.0.0.1/*", "https://10.0.0.1/*",
```

Save, then click **reload** on the extension's card.

## Prefer not to install an extension?

If you already use **uBlock Origin** or **Brave**, you can add the same rules as cosmetic filters
instead (uBlock: *Dashboard > My filters*; Brave: `brave://settings/shields/filters`, with
Developer mode on). Change the address to your router's:

```
192.168.0.1##div#cloud-login-msg
192.168.0.1###global-mask.cloud-login-msg
192.168.0.1##.cloud-dialog
```

## Popup still showing?

TP-Link changes the page between firmware versions, so a new version can bring the popup back.
Please [open an issue](../../issues) with:

- router model and firmware version (*Advanced > System > Firmware Update*),
- browser and version,
- a screenshot of the popup (blur anything personal).

If you know your way around DevTools, right-click the popup, **Inspect**, and include the `id` or
`class` of the popup's outer element. That is usually all it takes to fix.

## Not affiliated

This is an independent project by ZRoles Labs. It is not made, endorsed or supported by TP-Link.
"TP-Link" and "Archer" are trademarks of their owner and are used here only to say which routers
this works with.

## License

[MIT](LICENSE). Use it, change it, share it.
