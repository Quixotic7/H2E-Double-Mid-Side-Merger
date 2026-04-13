# `encode_doublems`

macOS command-line tool for combining Zoom H2essential front/rear stereo WAV pairs into a single 4-channel WAV.

It scans a folder recursively for matching files such as:

- `260405_125415_FRONT_RAW.WAV`
- `260405_125415_REAR_RAW.WAV`

and writes:

- `260405_125415_DUAL_MS_RAW.wav`

Channel order in the output WAV:

- `[0]` front left
- `[1]` front right
- `[2]` rear left
- `[3]` rear right

Usage:

```sh
./encode_doublems "/path/to/folder"
```

Optional flags:

```sh
./encode_doublems "/path/to/folder" --dry-run
./encode_doublems "/path/to/folder" --overwrite
```

Notes:

- Requires `ffmpeg` and `ffprobe` in `PATH`.
- Output is lossless PCM WAV using the same PCM codec and sample rate as the matched inputs.
- Metadata is copied from the `*_FRONT_RAW.wav` file.
