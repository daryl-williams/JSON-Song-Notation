# JSON Song Notation
The JSON Song Notation (or JSN) data structure is meant to be a simple representation of a song, defined as some number of measures, consisting of some number of beats per measure with each beat containing some number of voices, i.e. a chord or lyric or a symbolic representation of the beat itself among other possibilities.

Now there is a wealth of song material on the Internet and most every musician I know either carries a stack of binders or perhaps a tablet or computer with the songs that they will use for practive, or for a jam, or to entertain at open mics or even perform professionaly. Now these collection of songs are seldom repesented as full blown musical scores but rather as simple text with the lyrics and chords. But not all of these songs have neem created equaly and some are just downright wrong and need to be tweaked a bit at the very least, but at least they are usually in a plain text format and so it is possible. 

So I started looking around for a system that would allow for a more sophisticated way to create these simple song charts of lyric and chords, to ensure more accuracy from the begining. The long and short of it is I was not able to find anything that was simple enough to use for this purpose. Yes, there are many music notation systems out there, if you look. From full blown applications like [Sibelius](https://www.avid.com/sibelius), [Finale](https://www.finalemusic.com/), [MuseScore](https://musescore.org) and [LilyPond](https://lilypond.org/) to formats such as [ChordPro](https://www.chordpro.org), [abc notation](http://abcnotation.com/) and others but what I wanted was more than that; and I wanted it to be open source. Now programs like MuseScore and Lilipond are free and open source but they are far from easy, at least for me. And they are too sophisticated, being able to produce a full blown score of beautiful sheet music. All I wanted are chords and lyrics in an open data format. And that is where the JSON Song Notation format comes in to play.

A song written in JSN might be rendered in any number of formats or styles for example:

![Chord chart](http://weblane.com:3000/images//whiskey-for-breakfast-small.png) or perhaps as ![Chord chart](http://weblane.com:3000/images//wfb.png)

Depending on the client. To that end there is related project called SongWriter that is the proof of concept and initial reference implementation for the JSN client.

A song represented in JSN consists of a header which is a JSON object and a body which is a JSON array. The header contains song metadata and the body contains the measures and beats of the song. The song's measures are represented as an array and each array element is a beat and each beat is a JSON object containing some number of voices which are represented as the object's name/value pairs. The value of the voice is a simple lexical value, but that could could change in the future.

Following is a descriptive layout of the JSN format, representing an example song in 4/4 time with only one measure:

```json
{
	"header": {
		"key": "C",
		"title": "Rita Ballew",
		"composer": "Guy Clark",
		"capo_at_fret": "none",
		"time_signature": "4/4",
		"beats_per_bar": 4,
		"number_of_bars": "32",
		"tags": "Americana"
	},
	"body": [
		{
			"header": {},
			"beats": [
				{
			 		"chord": "C",
					"metric": 1,
					"lyric": "She"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "could"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "dance"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "that"
				}
			],
		},
		{
			"beats":[
				{
					"chord": "",
					"metric": 1,
					"lyric": "slow"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "U - "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "val - "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "de."
				}
			],
		},
		{
			"beats":[
				{
					"chord": "F",
					"metric": 1,
					"lyric": "Shuffle  "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "to "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "some  "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "cowboy  "
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "hustle "
				}, {
					"chord": "C",
					"metric": 1,
					"lyric": "how"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "she"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "made"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "them"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "cow -"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "boy,"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "buckles."
				}
			],
		},
		{
			"beats": [
				{
					"chord": "G",
					"metric": 1,
					"lyric": "shine"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "shine."
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "shine."
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}
			],
		},
		{
			"beats": [
				{
					"chord": "C",
					"metric": 1,
					"lyric": "Wild"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "eyed"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "and"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Mex -"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "ican"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "silv -"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "er"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "ed,"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "F",
					"metric": 1,
					"lyric": "trickin'"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "dumb"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "old"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "cousin"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "Wilard"
				}, {
					"chord": "C",
					"metric": 1,
					"lyric": "into"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "thinkin'"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "that"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "he"
				}, {
					"chord": "G",
					"metric": 1,
					"lyric": "got"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "her"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "this"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "C",
					"metric": 1,
					"lyric": "time."
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}
			],
		},
		{
			"beats": [
				{
					"chord": "F",
					"metric": 1,
					"lyric": "Hill"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "country   "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "honky"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "tonkin'  "
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "Ri -"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "ta"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Bal -"
				}, {
					"chord": "C",
					"metric": 1,
					"lyric": "lew"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "every"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "beer"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "joint"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "in"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "town"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "has"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "played"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "a"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "fool"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "for"
				}, {
					"chord": "G",
					"metric": 1,
					"lyric": "you."
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}
			],
		},
		{
			"beats": [
				{
					"chord": "F",
					"metric": 1,
					"lyric": "Back"
				},
				{
					"chord": "",
					"metric": 1,
					"lyric": "sliding"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "bar -"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "rel"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "ridin'"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Rita"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Bal - "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "lew,"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "C",
					"metric": 1,
					"lyric": "Ain't"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "a"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "cow -"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "boy"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "in"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Texas"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "would"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "not"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "G",
					"metric": 1,
					"lyric": "ride"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "a"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "bull"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "for"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "C",
					"metric": 1,
					"lyric": "you."
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}
			],
		},
		{
			"beats": [
				{
					"chord": "F",
					"metric": 1,
					"lyric": "So good  "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "luck"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Wilard"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "and"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "here's"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "to"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "you"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": " and "
				}
			],
		},
		{
			"beats":[
				{
					"chord": "Am",
					"metric": 1,
					"lyric": "here's"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "to  "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Rita"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "and I "
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "hope "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "she'll"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "do "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "you"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "G",
					"metric": 1,
					"lyric": "right"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "all "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "night "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "Lord"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "I "
				}, {
					"chord": "F",
					"metric": 1,
					"lyric": "wish "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "I "
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "was"
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": "the"
				}, {
					"chord": "G",
					"metric": 1,
					"lyric": "fool"
				}, {
					"chord": "",
					"metric": 1,
					"lyric": "in your "
				}, {
					"chord": "C",
					"metric": 1,
					"lyric": "shoes."
				}
			],
		},
		{
			"beats": [
				{
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}, {
					"chord": "",
					"metric": 1,
					"lyric": ""
				}
			]
		}
	]
}
```

