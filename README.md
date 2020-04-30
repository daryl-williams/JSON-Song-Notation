# JSON Song Notation
The JSON Song Notation (or JSN) data structure is meant to be a simple representation of a song, defined as some number of measures, consisting of some number of beats per measure with each beat containing some number of voices, i.e. a chord or lyric or a symbolic representation of the beat itself among other possibilities.

Now there is a wealth of song material on the Internet and most every musician I know either carries a stack of binders or perhaps a tablet or computer with the songs that they will use for practive, or for a jam, or to entertain at open mics or even perform professionaly. Now these collection of songs are seldom repesented as full blown musical scores but rather as simple text with the lyrics and chords. But not all of these songs have neem created equaly and some are just downright wrong and need to be tweaked a bit at the very least, but at least they are usually in a plain text format and so it is possible. 

So I started looking around for a system that would allow for a more sophisticated way to create these simple song charts of lyric and chords, to ensure more accuracy from the begining. The long and short of it is I was not able to find anything that was simple enough to use for this purpose. Yes, there are many music notation systems out there, if you look. From full blown applications like [Sibelius](https://www.avid.com/sibelius), [Finale](https://www.finalemusic.com/), [MuseScore](https://musescore.org) and [LilyPond](https://lilypond.org/) to formats such as [ChordPro](https://www.chordpro.org), [abc notation](http://abcnotation.com/) and others but what I wanted was more than that; and I wanted it to be open source. Now programs like MuseScore and Lilipond are free and open source but they are far from easy, at least for me. And they are too sophisticated, being able to produce a full blown score of beautiful sheet music. All I wanted are chords and lyrics in an open data format. And that is where the JSON Song Notation format comes in to play.

A song's lead sheet written in JSN may be rendered in any number of formats or styles for example:

![Lead Sheet](/images/twinkle-twinkle-jsn.png)

or perhaps the more familar:

![Lead Sheet](/images/twinkle-twinkle-lmss.png)

Depending on the client software. To that end there is related project called SongWriter that is the proof of concept and initial reference implementation for the JSN client that is comming soon.

A song represented in JSN consists of a header which is a JSON object and a body which is a JSON array. The header contains song metadata and the body is an array containing the measures and beats of the song. The song's measures are represented as a JSON object consisting of two JSON object. The first is an optional header (currently not used) and second is the "beats" object containing some number of voices which are represented as the object's name/value pairs. The value of the voice is a simple lexical value, but that could could change in the future.

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
		"beats_per_bar": "4",
		"number_of_bars": "1"
	},
	"body": [
		[{
			"chord": "C",
			"beat": "1",
			"lyric": "Twin - "
		}]
	]
}
```

Here is the full song rendered in JSN format: [Twinkle Twinkle Little Star](./jsn-example.txt)

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
			"metric": 1,
			"lyric": "Twin - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "kle, "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "twin - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "kle, "
		}],
		[{
			"chord": "F",
			"metric": 1,
			"lyric": "lit - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "tle "
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": "star,"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": ""
		}],
		[{
			"chord": "F",
			"metric": 14,
			"lyric": "How"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "I"
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": "won -"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": " der "
		}],
		[{
			"chord": "G7",
			"metric": 14,
			"lyric": "what"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "you"
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": "are."
		}, {
			"chord": "",
			"metric": 1,
			"lyric": ""
		}],
		[{
			"chord": "C",
			"metric": 1,
			"lyric": "Up"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "a - "
		}, {
			"chord": "F",
			"metric": 1,
			"lyric": "bove"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "the "
		}],
		[{
			"chord": "C",
			"metric": 14,
			"lyric": "world"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "so"
		}, {
			"chord": "G7",
			"metric": 1,
			"lyric": "high,"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": ""
		}],
		[{
			"chord": "C",
			"metric": 14,
			"lyric": "like"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "a"
		}, {
			"chord": "F",
			"metric": 1,
			"lyric": "dia - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "mond"
		}],
		[{
			"chord": "C",
			"metric": 1,
			"lyric": "in"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "the"
		}, {
			"chord": "G7",
			"metric": 1,
			"lyric": "sky."
		}, {
			"chord": "",
			"metric": 1,
			"lyric": ""
		}],
		[{
			"chord": "C",
			"metric": 1,
			"lyric": "Twin - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "kle"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "twin - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "kle"
		}],
		[{
			"chord": "F",
			"metric": 1,
			"lyric": "lit - "
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "tle"
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": "star"
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": ""
		}],
		[{
			"chord": "F",
			"metric": 14,
			"lyric": "How"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "I"
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": "won -"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": " der "
		}],
		[{
			"chord": "G7",
			"metric": 14,
			"lyric": "what"
		}, {
			"chord": "",
			"metric": 1,
			"lyric": "you"
		}, {
			"chord": "C",
			"metric": 1,
			"lyric": "are."
		}, {
			"chord": "",
			"metric": 1,
			"lyric": ""
		}]
	]
}
```

