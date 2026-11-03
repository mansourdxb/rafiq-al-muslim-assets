# video-bg — moving backgrounds for the verse video share

8-second portrait loops (720×1280, 24 fps H.264 CRF 29, no audio, ≤1 MB each, 14 clips), downloaded by the app on demand
(`client/src/lib/quran/videoBackgrounds.ts`; the first 3 are prefetched after install/update).

All clips are public domain (CC0) from Wikimedia Commons — sources in `CREDITS.json`.
Trimmed to 8 s, cropped to portrait and re-encoded; each was checked to contain no people.
