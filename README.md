# JSON Song Notation
The JSON Song Notation (or JSN from now on) data structure is meant to be a simple representation of a song, defined as some number of measures consisting of some number of beats per measure. Beyond this base structure the JSN format consists of some number of “voices”, each defined across each beat of each measure.

So a song represented as JSN consists of a header and body which are both JSON objects. The header contains song metadata and the body contains the measures and beats of the song. The song's measures are represented as an array and each array element counts as a beat and each beat is represented as an object containing a name value pair for that beat.

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
        "composer": "Traditional,
        "time-signature": 4,
        "number_of_measures": 1
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

