# Groceries — install notes

All seven files must sit in the **same folder**. Nothing else is needed.

```
index.html   manifest.json   sw.js
icon-180.png icon-192.png    icon-512.png   icon-maskable-512.png
```

## Getting it onto your phone

A service worker only runs over **HTTPS**. Opening `index.html` from your phone's
file manager won't work — it'll load, but it won't install or work offline.

**Easiest route — GitHub Pages, free and permanent:**

1. Create a repository (private is fine, Pages still works on free accounts for
   public repos — make it public if Pages is unavailable).
2. Upload all seven files to the root.
3. Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/root`.
4. Wait a minute, then open the `https://<you>.github.io/<repo>/` URL on your phone.

**Alternative:** drag the folder onto [Netlify Drop](https://app.netlify.com/drop).
No account needed for a first deploy.

## Installing

Open the URL in **Chrome on Android**, then menu (⋮) → *Add to Home screen* →
*Install*. It will appear as its own app with no browser bars.

Open it from the home-screen icon from then on, not from a browser tab. That's
what makes Android treat the storage as protected.

## Keeping your data safe

Three layers, in order of how much they matter:

1. **Install it.** Installed apps get persistent storage, so Android won't clear
   your data when space runs low. Setup shows whether protection is active.
2. **Export a backup.** Setup → *Export a backup file*. Do this after any big
   shop. Setup nags you once a month has passed.
3. **Keep a backup off the phone.** Email the file to yourself or drop it in
   cloud storage. A backup sitting in the phone's Downloads folder dies with the
   phone.

Restoring: Setup → *Restore from a backup* → pick the file. It replaces
everything currently stored, so export first if you're unsure.

## Moving your test data across

Data you entered while testing lives in a different storage area from the
installed app. It does **not** carry over. If you want to keep those prices,
export from where you tested first, then restore into the installed app.

If it was only a couple of trial runs, starting clean is simpler.

## Updating the app later

When `index.html` changes:

1. Replace the file on the host.
2. Bump the version in `sw.js` — change `groceries-v1` to `groceries-v2`.

Without the version bump, phones keep serving the cached copy. Your data is
untouched by updates either way; it lives separately from the cached files.
