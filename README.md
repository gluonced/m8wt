# M8 Wavetable Patcher

A single-page, client-side tool for replacing the built-in WAVSYNTH wavetables and their names in Dirtywave M8 firmware `.hex` files.

Everything runs in the browser. Nothing is uploaded, and this repository contains no firmware, wavetable data or wavetable names, only the code that reads and patches a firmware file you provide.

## Use

1. **Load firmware**: pick the hardware (Headless, Model 01, Model 02), then choose a firmware `.hex`. Its 61 wavetables (shapes `09`–`45`) and names are read into the buffer.
2. Select a shape to rename it (12 characters after `WT-`: letters, numbers, `:` and `-`), view all 64 frames, and audition it with **Travel** (scans frames 1→64 over the set time) or **Toggle** (loops the frame chosen with the slider).
3. **Load wavetable** replaces the selected shape with a WAV. Other formats are converted (with a warning first), and files that aren't 64 frames × 256 samples can be resampled by entering their frame count or frame length.
4. **Export wavetable** saves the selected shape as unsigned 8-bit (the M8's format) or signed 16-bit WAV.
5. **Patch** asks for the firmware to write into (it can be a different model or version), then saves a new `.hex`. Only the 61 names and wavetables change, and every other byte is verified unchanged before saving.

Known layouts: Headless 6.5.2C, Model 01 6.6.2A, Model 02 6.6.2A. Other versions are located by searching the file and verified before use.

## Host on GitHub Pages

1. Create a repository and add `index.html` (and this README) to the root.
2. In the repository, open **Settings → Pages**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, and save.
3. The site appears at `https://<username>.github.io/<repository>/` after a minute or two.

## Notes

- **Patch** opens a native "Save as" window in Chrome and Edge. Firefox and Safari don't support that yet, so the file is downloaded instead.
- Playback uses a fixed pitch of C-4 (261.63 Hz).
- Not affiliated with Dirtywave. Flash modified firmware at your own risk, and make sure you can restore the official firmware first.
