# M8 LPP Recap

## Introduction

The Launchpad Pro MK3 (LPP) is more than just an extension of your M8.

It's more buttons, more pads and LEDs: you can start an operation on the M8 and finish it on the LPP or conversely. For example Play on the LPP is Play on the M8.

But there are also features that are only available with the LPP, like the Beat Repeat thing.

## Prerequisites

Update your LPP with Components, plug MIDI IO into each other (Out1 for the LPP), choose `LAUNCHPAD PRO` in your `CTRL SURFACE` MIDI Settings.

## Hardware description

```
Shift  <  >  Sess Note  -  -  Seq Prj   Nov
      +------------------------------+
 Up   |                              | ->
Down  |                              | ->
 Clr  |                              | ->
Dupe  |                              | ->
  -   |                              | ->
  -   |                              | ->
Play  |                              | ->
Edit  |                              | ->
      +------------------------------+
Setup  T1  T2  T3  T4  T5  T6  T7  T8
     SShot  M   S   -   -   -   -   -
```

* `Sess` : Session
* `Nov` : Novation Logo (Live Mode indicator)
* `Clr` : Clear
* `Dupe` : Duplicate
* `T1` to `T8` : Track buttons
* `Edit` (Rec/Capture MIDI button) : Edit Mode
* `SShot` (RecArm button) : Snapshot
* `->` : Row buttons
* `M`/`S` : Mute/Solo

## Global actions
 
* `Sess` : Session View
* `Shift` + `Sess` : Beat Repeat View
* `Note` : Keyboard View
* `Seq` : Sequencer View
* `<`/`>`, except in Session View : Select current track of the keyboard pads, T1-T8 buttons momentarily show the current track
* `Play` : like Play on the M8
* `Edit`, except in Keyboard View : Edit Mode
* `Shift` + `SShot` : Store Snapshot
* `SShot` : recall Snapshot
* `M` : Mute tracks (use T1-T8), when blinking the mutes are momentary
* `S` : Solo tracks (use T1-T8), when blinking the solos are momentary

File Browser : `Up`/`Down` is Up/Down, `<`/`>` are first/last entry in the directory, `Shift` for Yes (no confirmation asked when loading songs!), `Play` to preview a song or an instrument.

## Session View

### Play Mode

* Display
  * White pads : non empty chains
  * Dark pink pads : empty chains
  * Green pads : chains currently playing
  * Blinking green pads : cued chains
  * Blinking blue pad : cursor (Edit mode only)
* Actions
  * `Prj` : load a M8 Song (`.m8s`), see File Browser above, Prj again to cancel
  * `Play` : play current row
  * `Up`/`Down` : scroll (LPP span is shown on the M8 with square brackets)
  * `Shift` + `Up`/`Down` : scroll by pages (eight rows)
  * `->` : play or cue rows
  * `Shift` + `<` : Live Mode toggle

### Edit Mode

* Edited chain makes same chains blink.
* Double tap on a chain : Edit it in Sequencer View, M8 shows the edited phrase
* Hold `Dupe` + pad, then tap an empty pad : copy-paste
* Hold `Dupe` + pad, then double tap an empty pad or a non empty pad : deep clone
* Hold `Dupe` + row, then tap a row : copy and insert
* Hold `Clr` + pad or row : clear pad or row

## Beat Repeat View

* M8 must be playing.
* Lines 6 and 7 : set a range with two pads, or just one pad, to repeat this range
* Line 8 : select the tracks which will be affected by the repeat, the others will continue normally

## Note View

Notes are sent to the current track.

### Layout

* White pads : show the octaves of the first non empty note of the current scale
* Green pads : note currently played (can be several for Hypersynth)

If the scale has 12 notes the note above a pad is 5 notes above (perfect fourth for the usual chromatic scale).

### Actions

* `Prj` : load an instrument file (`.m8i`) for the keyboard (plays on the current track), see File Browser above.
* `Up`/`Down` : scroll
* `Shift` + `Up`/`Down` : load an instrument from the pool
* `Rec` + `Play` : record keyboard notes (MIDI notes???) in current phrase with the current instrument

## Sequencer View

### Layout

```
N N N N   P P P P
N N N N   P P P P
N N N N   P P P P
N N N N   P P P P

K K K K   K K K K
K K K K   K K K K
K K K K   K K K K
K K K K   K K K K
```

* `N` : notes in the current phrase
* `P` : phrases in the current chain
* `K` : keyboard, scrollable with Up and Down

### Both Mode

* `Prj` : load an instrument file (`.m8i`) for the keyboard (plays on the current track), see File Browser above.

### Play Mode

`Clr` and `Dupe` work the habitual way.

### Edit Mode

Hold a note :

* `->` represent the velocities
* `Up`/`Down` : octave shift
* keyboard pad : set the note in the current note slot
* hold `Shift` to browse the instrument pool, then release Shift to choose

Hold a phrase:

* `Play` : loop this phrase
* `Up`/`Down` : set the transposition

