# Exploring Roland GO:KEYS and GO:PIANO. 

Roland GO:PIANO and GO:KEYS are derived from Roland Juno-DS. Apparently, when Roland released these entry-level keyboards in 2017, it re-used what was developed for Juno-DS released in 2015. Consequently, the GO-keyboards share many of the core capabilities with their advanced and rather more expensive sibling.
This repository documents my ongoing findings and notes of my discoveries about these extra-portable and affordable instruments.

## 1. Preset sounds
GO:KEYS and GO:PIANO have all the sounds from Juno-DS "PRST" bank, except the last six. Both have full set of GM2 sounds. Sounds form Juno-DS "DS" bank are not included, the bank has been re-used for GO:PIANO sounds which seem to be different from PRST and GM2 sounds. See [full list](doc/GO-sounds.md) of preset sounds.

## 2. Channel allocation
Choosing instrument category from GO:KEYS touch panel changes used MIDI channel. 

|Ch# |Part        |Allocation|
|----|------------|----------|
| 1  |  PIANO     | Panel    |
| 2  |  ORGAN     | Panel    |
| 3  |  STRINGS   | Panel    |
| 4  |  BRASS     | Panel    |
| 5  |  BASS      | Panel    |
| 6  |  SYNTH     | Panel    |
| 7  |  FX/GUITAR | Panel    |
| 8  |  Bass      | Loop Mix |
| 9  |  Part A    | Loop Mix |
|10  |  DRUM      | Panel    |
|11  |  Part B    | Loop Mix |
|12  |  Part X    | Loop Mix |
|13  |  Part X    | Loop Mix |
|14  |  Part X    | Loop Mix |
|15  |  Part X    | Loop Mix |
|16  |  Drum      | Loop Mix |

GO:PIANO keypresses generate MIDI events always on channel 1.

## 3. Demo songs
GO:KEYS has five demo songs.
For playing the first one, send the following SysEx strings:
```
f0 41 10 00 00 00 28 12 01 00 02 10 00 00 00 00 f7
f0 41 10 00 00 00 28 12 01 00 05 05  00 00 f7
```

(first one selectis the song, the second one triggers start/stop)
Second song:
```
f0 41 10 00 00 00 28 12 01 00 02 10 00 00 01 00 f7
```

## 4. Sound tweaking
Both keyboards respond to many effects-related CC commands (e.g portamento, vibrato, filter settings etc.) 
- CC 5 - Portamento time
- CC 7 - Volume
- CC 10 - Pan
- CC 11 - Expression
- CC 65 - Portamento on/off
- CC 71 - Filter Resonance
- CC 72 - Release Time
- CC 73 - Attack Time
- CC 74 - Filter Cutoff
- CC 75 - Decay Time
- CC 76 - Vibrato Rate
- CC 77 - Vibrato Depth
- CC 78 - Vibrato Delay
- CC 91 - Reverb Send
- CC 93 - Chorus Send
- CC 126 - Mono Operation
- CC 127 - Poly Operation

## 5.  GO:PIANO has the same loop mixing fun as GO:KEYS!
Loop mix modes can be changed and triggered either by using MIDI NRPN commands or via SysEx. NRPN numbers can be found in gokeys-scratch-extension repository. SySex string for GO:PIANO:
```
f0  41 10 00 00 00 3C 12 01 00 00 19 01 00 f7
```

## 5. Sound layering
Up to 16 sounds can be played at the same time. See the [SendMIDI](https://github.com/gbevin/SendMIDI) script [here](examples/layering-ep-wind) for an example

## 6. Custom patches!
It is possible to upload custom patches to GO-keyboards. 


