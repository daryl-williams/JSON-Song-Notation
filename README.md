# JSON Song Notation
The JSON Song Notation (or JSN) data structure is meant to be a simple representation of a song, defined as some number of measures, consisting of some number of beats per measure with each beat containing some number of voices, i.e. a chord or lyric or a symbolic representation of the beat itself among other possibilities.

# Motivation
Now there is a wealth of song material on the Internet and most every musician I know either carries a stack of binders or perhaps a tablet or computer with the songs that they will use for practive, or for a jam, or to entertain at open mics or even perform professionaly. Now these collection of songs are seldom repesented as full blown musical scores but rather as simple text with the lyrics and chords. But not all of these songs have neem created equaly and some are just downright wrong and need to be tweaked a bit at the very least, but at least they are usually in a plain text format and so it is possible. 

So I started looking around for a system that would allow for a more sophisticated way to create these simple song charts of lyric and chords, to ensure more accuracy from the begining. The long and short of it is I was not able to find anything that was simple enough to use for this purpose. Yes, there are many music notation systems out there, from full blown, proprietary  applications like [Dorico](https://new.steinberg.net/dorico/), [Sibelius](https://www.avid.com/sibelius), [Finale](https://www.finalemusic.com/), [Band-in-a-Box](https://www.pgmusic.com/), [Noteflight](https://www.noteflight.com/), [Flat](https://flat.io/) to open source programs such as  [MuseScore](https://musescore.org), [LilyPond](https://lilypond.org/), [Chordii](https://www.vromans.org/johan/projects/Chordii/intro.html). These applications are very powerful and sophisticated, being able to produce full blown scores of beautiful sheet music, and they are hard to use, at least for me. All I want is a simple lead sheet with the chords and lyrics in an open data format.  Now there are also open source notation formats such as [ChordPro](https://www.chordpro.org) and [abc notation](http://abcnotation.com/) that help in writing lead sheets but what I wanted was more than that; I want an open source machine readable format, i.e. a data structure that can be used to build music applications; imagine an open source version of Band-in-a-Box! (who doesn't love BIAB)?  And that is where the JSON Song Notation format comes in to play.

# Objective
A song's lead sheet written in JSN may be rendered in any number of formats or styles for example:

![Lead Sheet](/images/twinkle-twinkle-jsn.png)

or perhaps the more familar:

![Lead Sheet](/images/twinkle-twinkle-lmss.png)

Depending on the client software. To that end there is related project called SongWriter that is the proof of concept and initial reference implementation for the JSN client that is comming soon.

# Technical Details
A song expressed in JSN consists of a header (a JSON object) and a body (a JSON array). The header contains song metadata such as title, composer, key, time signature, number of measures, etc. and the body is an array containing the measures and beats of the song. Each measure contains an array of beats and each beat (a JSON ojbect) contains some number of "voices" that occur during that beat, i.e. a chord, lyric, etc. The value of a "voice" is a simple lexical value.

The following very simple example defines a full (if very short) song defined as a JSN structure with only one measure from the song Twinkle, Twinkle Little Star:

```json
{
  "header": {
    "key": "C",
    "tags": "",
    "title": "Twinkle Twinkle",
    "composer": "Traditional",
    "capo_at_fret": "",
    "time_signature": "4/4",
    "beats_per_bar": 4,
    "number_of_bars": 12
  },
  "body": [
    [
      {"chord": "C"}, {"beat":1}, {"lyric": "Twin -"},
      {"chord": ""},  {"beat":1}, {"lyric": "kle, "},
      {"chord": ""},  {"beat":1}, {"lyric": "twin -"},
      {"chord": ""},  {"beat":1}, {"lyric": "kle, "}
    ]
  ]
}
```

Here is the full song rendered in JSN format: [Twinkle Twinkle Little Star](./jsn-example-v1.txt).

Or view the whole song here:

```json
{
	"header": {
		"key": "C",
		"tags": "",
		"title": "Twinkle Twinkle",
		"composer": "Traditional",
		"capo_at_fret": "",
		"time_signature": "4\/4",
		"beats_per_bar": 4,
		"number_of_bars": 12
	},
	"body": [
		[{
			"chord": "C",
			"beat": 1,
			"lyric": "Twin - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "kle, "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "twin - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "kle, "
		}],
		[{
			"chord": "F",
			"beat": 1,
			"lyric": "lit - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "tle "
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": "star,"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": ""
		}],
		[{
			"chord": "F",
			"beat": 14,
			"lyric": "How"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "I"
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": "won -"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": " der "
		}],
		[{
			"chord": "G7",
			"beat": 14,
			"lyric": "what"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "you"
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": "are."
		}, {
			"chord": "",
			"beat": 1,
			"lyric": ""
		}],
		[{
			"chord": "C",
			"beat": 1,
			"lyric": "Up"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "a - "
		}, {
			"chord": "F",
			"beat": 1,
			"lyric": "bove"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "the "
		}],
		[{
			"chord": "C",
			"beat": 14,
			"lyric": "world"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "so"
		}, {
			"chord": "G7",
			"beat": 1,
			"lyric": "high,"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": ""
		}],
		[{
			"chord": "C",
			"beat": 14,
			"lyric": "like"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "a"
		}, {
			"chord": "F",
			"beat": 1,
			"lyric": "dia - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "mond"
		}],
		[{
			"chord": "C",
			"beat": 1,
			"lyric": "in"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "the"
		}, {
			"chord": "G7",
			"beat": 1,
			"lyric": "sky."
		}, {
			"chord": "",
			"beat": 1,
			"lyric": ""
		}],
		[{
			"chord": "C",
			"beat": 1,
			"lyric": "Twin - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "kle"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "twin - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "kle"
		}],
		[{
			"chord": "F",
			"beat": 1,
			"lyric": "lit - "
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "tle"
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": "star"
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": ""
		}],
		[{
			"chord": "F",
			"beat": 14,
			"lyric": "How"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "I"
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": "won -"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": " der "
		}],
		[{
			"chord": "G7",
			"beat": 14,
			"lyric": "what"
		}, {
			"chord": "",
			"beat": 1,
			"lyric": "you"
		}, {
			"chord": "C",
			"beat": 1,
			"lyric": "are."
		}, {
			"chord": "",
			"beat": 1,
			"lyric": ""
		}]
	]
}
```

