# Encode Double MS

This was quickly vibe-coded using Codex. 

# Use the Zoom H2essential as a horizontal ambisonic mic

Unlike the predecessor to the Zoom H2essential, the Zoom H2N, the H2E does not have a mode to record to AmbiX. 

However the Zoom H2E can record to two separate mid side raw stereo files. One using the front mic as the mid and the other using the back mic as the mid. 

This is called Double Mid Side and can be used with a plugin like [ab Encoder MS](https://www.audiobrewers.com/tech-support/audio-brewers-ab-encoder-ms) to turn it into a Ambisonic format. This plugin is $15 and does a great job!

Once in a Ambisonic format you can use the audio with plugins like Rode Soundfield(My favorite) to rotate, change mic pickup patterns, and refocus the audio or dearVR Ambi Micro or any other number of Ambisonic binuaral decoder plugins to turn it in to 3d sounding binaural audio. 

The Ambisonic format is incredibly useful and really makes the Zoom H2N a pocketable swiss army knife of recorders!

The problem is that being 2 separate audio tracks makes the audio a bit tricky to work with, you need to manually split the audio in Reaper and recombine to a 4 channel track. While this process is super easy to do, it is annoying to have to do over and over. 

So the purpose of this tool is to quickly give you a full lossless 4 track audio file that is quick to work with. 


# What does this do?

macOS command-line tool for combining Zoom H2essential front/rear stereo mid side raw WAV pairs into a single 4-channel WAV.

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
