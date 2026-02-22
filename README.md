# M8 LPP Recap

## Introduction

The Launchpad Pro MK3 (LPP) is more than just an extension of your M8.

It's more buttons, more pads and LEDs: you can start an operation on the M8 and finish it on the LPP or conversely. For example Play on the LPP is Play on the M8.

But there are also features that are only available with the LPP, like the Beat Repeat thing.

## Prerequisites

1. Update your LPP with Components.
2. Connect the two devices (plug MIDI IO into each other, Out1 for the LPP, or use your prefered MIDI over USB router and be sure to use the LPP port named "Launchpad Pro MK3 LPProMK3 MIDI", it should be the first one).
3. Choose `LAUNCHPAD PRO` in `CTRL SURFACE` on your MIDI Settings.

Please be aware that:

- channel 1 is used from LPP to M8 to send CC messages (#1 to #98),
- channels 1,2 and 3 are used from M8 to LPP to update the LEDs and pads (2 is for blinking, 3 for pulsing).

This cannot be changed.

Mode details in the [Programmer’s reference manual](https://fael-downloads-prod.focusrite.com/customer/prod/s3fs-public/downloads/LPP3_prog_ref_guide_200415.pdf) of the LPP, or at the bottom of this document.

## Hardware description

```
Shift < > Sess Note - - Seq Prj Nov
      +-----------------------+
 Up   |                       | ->
Down  |                       | ->
 Clr  |                       | ->
Dupe  |                       | ->
  -   |                       | ->
  -   |                       | ->
Play  |                       | ->
Edit  |                       | ->
      +-----------------------+
Setup  T1 T2 T3 T4 T5 T6 T7 T8
     SShot M  S  -  -  -  -  -
```

* `Sess` : Session
* `Seq` : Sequencer
* `Nov` : Novation Logo (Live Mode indicator)
* `Clr` : Clear
* `Dupe` : Duplicate
* `T1` to `T8` : Track buttons
* `Edit` (Rec/Capture MIDI button) : Edit Mode
* `SShot` (Record Arm button) : Snapshot
* `->` : Row buttons
* `M`/`S` : Mute/Solo

## Global actions
 
* `Sess` : Session View
* `Shift` + `Sess` : Beat Repeat View
* `Note` : Keyboard View
* `Seq` : Sequencer View
* `<` or `>`, except in Session View : Select current track of the keyboard pads,
  T1-T8 buttons momentarily show the current track
  (Keyboard view can access any track, Seq view can only access non empty tracks)
* `Edit`+`Play`, except in Session View : record the keyboard notes in the current track with the current instrument
* `Play` : like Play on the M8
* `Edit`, except in Keyboard View : Edit Mode
* `Shift` + `SShot` : Store Snapshot
* `SShot` : recall Snapshot
* `M` : Mute tracks (use T1-T8), when blinking the mutes are momentary
* `S` : Solo tracks (use T1-T8), when blinking the solos are momentary

Please note that momentary Mutes or Solos can be inverted if you Mute/Solo a track statically then push the Mute or Solo button for momentary Mutes/Solos.

File Browser : `Up` or `Down` is Up or Down, `<` or `>` are first or last entry in the directory, `Shift` for Yes (no confirmation asked when loading songs!), `Play` to preview a song or an instrument.

## Session View

M8 screen shows the Song view.

### Play Mode

* Display
  * White pads : non empty chains
  * Dark pink pads : empty chains
  * Bright pink : bookmarked chains
  * Green pads : chains currently playing (dimmer for empty chains)
  * Blinking green pads : cued chains
  * Blinking blue pad : cursor (Edit mode only)
* Actions
  * `Prj` : load a M8 Song (`.m8s`), see File Browser above, Prj again to cancel
  * `Play` : play current row
  * `Up`/`Down` : scroll (LPP span is shown on the M8 with square brackets)
  * `Shift` + `Up`/`Down` : scroll by pages (eight rows)
  * `->` : play or cue rows
  * `Shift` + `<` : Live Mode toggle (Novation logo is lit)

### Edit Mode

* Edited chain makes same chains blink.
* Double tap on a chain : Edit it in Sequencer View, the M8 screen shows the edited phrase
* Hold `Dupe` + pad, then tap an empty pad : copy-paste
* Hold `Dupe` + pad, then double tap an empty pad or a non empty pad : deep clone
* Hold `Dupe` + row, then tap a row : copy and insert
* Hold `Clr` + pad or row : clear pad or row

## Beat Repeat View

* M8 must be playing.
* Lines 6 and 7 : set a range with two pads, or just one pad, to repeat this range
* Line 8 : select the tracks which will be affected by the repeat, the others will continue normally

## Note View

Notes are sent to the current track (the relevant Track button is lit).

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

M8 screen shows the Phrase view.

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
* `K` : keyboard, scrollable with `Up` and `Down` (see Keyboard view above)

### Both Mode

* `Prj` : load an instrument file (`.m8i`) for the keyboard (plays on the current track), see File Browser above.

### Play Mode

`Clr` and `Dupe` work the habitual way.

### Edit Mode

* `Shift`+`<` or `>` : rotate notes in the phrase
* tap an empty pad :
  * create a note in the left corner
  * create a phrase in the right corner (like `Edit`+`Edit`)

Hold a note :

* `->` represent the velocities
* `Up` or `Down` : octave shift
* keyboard pad : set the note in the current note slot
* hold `Shift` to browse the instrument pool, then release Shift to choose

Hold a phrase:

* `Play` : loop this phrase
* `Up`/`Down` : set the transposition

## Technical details

### CCs sent by the LPP

On channel one we have these CCs:

```
90 91 92 93 94 95 96 97 98
80 81 82 83 84 85 86 87 88 89
70 71 72 73 74 75 76 77 78 79
60 61 62 63 64 65 66 67 68 69
50 51 52 53 54 55 56 57 58 59
40 41 42 43 44 45 46 47 48 49
30 31 32 33 34 35 36 37 38 39
20 21 22 23 24 25 26 27 28 29
10 11 12 13 14 15 16 17 18 19
  101 .2 .3 .4 .5 .6 .7 .8    . for 10
    1  2  3  4  5  6  7  8
```

A press is value 127 and a release is 0. Then the M8 interprets them and sends back notes to the LPP to update its state.
