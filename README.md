# Aql

A minimal Android wrapper (WebView) around the Aql chat-app UI in
`app/src/main/assets/index.html`. App name: **Aql**, package id:
`com.aqil.aql`.

## Download the debug APK

Every push to `main` builds a debug APK via GitHub Actions (workflow:
**Build debug APK**). Open the latest run on the **Actions** tab and
download the artifact named **aql-debug-apk** (requires being signed in
to GitHub). No release is published; debug keystore only.

## Notes

- The top tok/s counter is a **real measurement**: during streaming it
  counts the tokens actually rendered and divides by the elapsed
  generation time, updating live. No random numbers, no fake jitter.
  When a real streaming API is wired later, the same counter code must
  use real chunk timing.
- The **Usage** button (in the model row, with an in/out/cache icon: an
  arrow entering a cache tray and an arrow leaving it) opens a usage
  view with input tokens, output tokens, cached tokens and cache
  percentage. Numbers come only from real measurement: local counting
  of text actually sent and rendered in demo mode, or the `usage`
  object of a real API response when wired (OpenAI-style fields plus
  DeepSeek's `prompt_cache_hit_tokens` / `prompt_tokens_details.
  cached_tokens`). Cache is 0 in demo mode because no real cache exists
  there — never fabricated.
- The **+ button** sits inside the composer row at its trailing end,
  next to the text field, with mic and send/stop beside it (like the
  Muse app's own composer — not floating, not at the old paperclip
  spot). Its menu offers working uploads: pick an image or a file from
  the device and it attaches to the message; the mic button attaches an
  audio clip the same way. The wrapper implements the WebView file
  chooser, so these inputs work on-device.
- No API keys, secrets, or credentials are included in this repo. Any
  key fields in the UI ship empty; the user enters their own key
  on-device.
- This project is separate from Lotus. Nothing here touches Lotus
  files, repos, or designs.
