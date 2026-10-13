# Kurdish TV for iPhone (PWA)

A mobile web-app version of the Kurdish TV player, with the TV-style dark layout, live screen, channel banner, aspect ratio selector, category/search guide, favourites and remembered last channel. It contains the 35 channel links supplied in the conversation. Arabic TV and the Windows Kurdish TV app are not changed.

## Install on iPhone — no Apple Developer account

This is a PWA (web app), not an iPhone `.ipa` or a Windows `.exe`. It must be served from an HTTPS website before iOS can add it to the Home Screen.

1. Publish the contents of this folder to an HTTPS static host (for example, GitHub Pages, Cloudflare Pages or Netlify). The host must serve `index.html` at the site root and preserve the other files alongside it.
2. On iPhone, open the HTTPS address in **Safari**.
3. Tap **Share** → **Add to Home Screen**. If offered, turn on **Open as Web App**, then tap **Add**.
4. Launch **Kurdish TV** from the new Home Screen icon. Internet is required for live channels.

No paid Apple Developer account is needed for this method. A web app cannot be placed in the App Store as a native app without Apple's normal developer process.

## Important iPhone streaming limitations

- iPhone Safari plays many HLS (`.m3u8`) streams natively, but broadcasters may change or disable public links at any time.
- The browser version cannot set arbitrary HTTP `Referer` or User-Agent headers. **Zoom TV Kurdish** in the supplied playlist specifically uses a referrer, so it may not play in this PWA. Some other channels may block Safari, iOS, or your region.
- Playback starts after a tap if iOS blocks autoplay. HEVC support depends on the iPhone model and stream.
- The aspect selector affects the video container and fitting, but iOS Safari may constrain how video is displayed in its native fullscreen mode.

## Local preview

For a quick desktop preview, serve this directory with any static web server. For example, from this directory run `python -m http.server 8000`, then visit `http://localhost:8000`. Service-worker installation and iPhone Home Screen installation require HTTPS (localhost is a special development exception).

## Updating channels

Edit `channels.js`. Each channel has `name`, `group`, `logo`, and `url`. Do not include channels unless you are entitled to access them; this app only provides a player for the public stream URLs supplied by the user.
