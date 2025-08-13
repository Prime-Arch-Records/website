# Prime Arch Records – Static Site

A minimal static site for the label **Prime Arch Records**. Host on GitHub Pages with a custom domain.

## Structure
```
/
  index.html
  /assets
    style.css
    logo.svg
    /covers       # add your 3000x3000 JPGs here
    /icons        # favicon + webmanifest
  /songs          # put your MP3 (320 kbps), WAV, and lyrics PDFs here
  /docs           # license and welcome
  /scripts
```

## Add a song
1. Duplicate the `<!-- SONG TEMPLATE -->` block in `index.html`.
2. Replace placeholders: title, mood/BPM, Spotify link, file paths and Plausible props.
3. Drop your cover in `assets/covers/` and audio/PDF in `songs/`.

## Deploy (GitHub Pages)
- Settings → Pages → Deploy from `main` → Root `/`.
- Set custom domain: `primearchrecords.com` and add a `CNAME` DNS record pointing to `<user>.github.io`.

## Analytics
Using [Plausible] with custom events already wired to the buttons via `onclick`.

## Convert audio to 320 kbps MP3 (from WAV)
Use `ffmpeg` locally:
```
ffmpeg -i "input.wav" -c:a libmp3lame -b:a 320k -ar 44100 -map_metadata 0 "output-320.mp3"
```
Batch example (macOS/Linux bash):
```
for f in *.wav; do ffmpeg -i "$f" -c:a libmp3lame -b:a 320k -ar 44100 -map_metadata 0 "${f%.wav}-320.mp3"; done
```

> Tip: Keep original WAV in `/songs/` and name MP3 the same stem for easy linking.

## License
See `/docs/welcome-license.md`.
