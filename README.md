# JSON Song Notation
The JSON Song Notation (or JSN from now on) data structure is meant to be a simple representation of a song, defined as some number of measures, consisting of some number of beats per measure with each beat containing some number of voices, i.e. a chord or lyric or a symbolic representation of the beat itself among other possibilities.

Now there is a wealth of song material on the Internet and most every musician I know either carries a stack of binders or perhaps a tablet or computer with the songs that they will use for practive, or for a jam, or to entertain at open mics or even perform professionaly. Now these collection of songs are seldom repesented as full blown musical scores but rather as simple text with the lyrics and chords. But not all of these songs have neem created equaly and some are just downright wrong and need to be tweaked a bit at the very least, but at least they are usually in a plain text format and so it is possible. 

So I started looking around for a system that would allow for a more sophisticated way to create these simple song charts of lyric and chords, to ensure more accuracy from the begining. The long and short of it is I was not able to find anything that was simple enough to use for this purpose.

Now there are many music notation systems out there, if you look. From full blown applications like [Sibelius](https://www.avid.com/sibelius), [Finale](https://www.finalemusic.com/), [MuseScore](https://musescore.org) and [LilyPond](https://lilypond.org/) to formats such as [ChordPro](https://www.chordpro.org), [abc notation](http://abcnotation.com/) and others but what I wanted was more than that; and I wanted it to be open source. Now programs like MuseScore and Lilipond are free and open source but they are far from easy, at least for me. And they are too sophisticated, being able to produce a full blown score of beautiful sheet music. All I wanted are chords and lyrics in an open data format. And that is where JSON Song Notation comes in.

So a song represented as JSN consists of a header and body which are both JSON objects. The header contains song metadata and the body contains the measures and beats of the song. The song's measures are represented as an array and each array element counts as a beat and each beat is represented as an array containing some number of Javascript objects each one representing one voice that occur on that beat.

A song written in JSN might be rendered in any number of formats or styles for example:

![Chord chart](http://weblane.com:3000/images//whiskey-for-breakfast-small.png) or perhaps as ![Chord chart](http://weblane.com:3000/images//wfb.png)

Depending on the client. To that end there is related project called SongWriter that is the proof of concept and initial reference implementation fora JSN client.

Following is a descriptive layout of the JSN format, representing an example song in 4/4 time with only one measure:

```json
Example song using JSN format:

{
 "header": {
        "key": "C",
        "title": "Twinkle Twinkle Little Star",
        "composer": "Traditional",
        "time-signature": 4,
        "number-of-measures": 1
    },
    "body": {
        "measures": [
            [{
                "beat1": {
                    "voice1": "C",
                    "voice2": "/",
                    "voice3": "Twinkle"
                }
            }, {
                "beat2": {
                    "voice1": "",
                    "voice2": "/",
                    "voice3": "twinkle"
                }
            }, {
                "beat3": {
                    "voice1": "F",
                    "voice2": "/",
                    "voice3": "little"
                }
            }, {
                "beat4": {
                    "voice1": "",
                    "voice2": "/",
                    "voice3": "star"
                }
            }]
        ]
    }
}
```

