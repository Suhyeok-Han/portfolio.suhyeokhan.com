Place 12 compressed audio files in `compressed/`.

Expected filenames:

- `compressed/track-01.mp3` — 1:00 / 13:00
- `compressed/track-02.mp3` — 2:00 / 14:00
- `compressed/track-03.mp3` — 3:00 / 15:00
- `compressed/track-04.mp3` — 4:00 / 16:00
- `compressed/track-05.mp3` — 5:00 / 17:00
- `compressed/track-06.mp3` — 6:00 / 18:00
- `compressed/track-07.mp3` — 7:00 / 19:00
- `compressed/track-08.mp3` — 8:00 / 20:00
- `compressed/track-09.mp3` — 9:00 / 21:00
- `compressed/track-10.mp3` — 10:00 / 22:00
- `compressed/track-11.mp3` — 11:00 / 23:00
- `compressed/track-12.mp3` — 12:00 / 0:00

The current files are encoded as 64kbps MP3 for lighter site delivery. Keep source `Track_*.mp3` files local; they are ignored by git.

Browser audio policy requires one click before sound can start. The page shows a small `Enable Sound` button for that first gesture.

Audio is loaded only after that click, so the first visual render is not blocked by these larger files.
