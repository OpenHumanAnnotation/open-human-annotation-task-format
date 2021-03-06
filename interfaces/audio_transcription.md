# Audio Transcription

The `audio_transcription` interface allows you to convert audio into transcribed text.

- Markdown description containing images, links or instructions. Per-task and/or universal description.

## Schema

```javascript
{
  "interface": {
    "type": "audio_transcription",
    "description": "MarkdownDescription",
    "language"?: LanguageString, // defaults to english
    "phraseBank"?: UrlToCSV,
    "onlyUseWordsInPhraseBank": boolean, // defaults to false
    "transcriptionType": "simple" | "proper" //defaults to simple
  },
  "samples": [
    {
      audioUrl: "https://...."
    }
  ],
  "examples": [
    {
      audioUrl: "https://...",
      annotation: "..."
    }
  ]
}
```

## Annotation

Each task annotation is a string representation of an audio file. The annotation format is determined by `interface.transcriptionType`.

## Simple Transcription Type

- All numbers written in their full string form. e.g. 100 is written one hundred. This is because numbers can be pronounced in different ways, e.g. one thousand five hundred and fifteen hundred. [There are libraries to convert number words to numbers](https://pypi.org/project/word2number/)
- All characters are lower case.
- In general, punctuation such as commas, hyphens, apostrophes and ellipses are not present. Periods and question marks should be kept. If a hyphen-word is used, a dash "-" should be used instead of a unicode hyphen "‐"
- If a letter is spoken e.g. "ABC" it's written as "ABC"
- Space after every comma
- All sentences have a period

```
// Example Simple Transcription Strings

my favorite song has the letters ABC in it.
there are one hundred ways to make a mistake.
```

## Proper Transcription Type

- All numbers written in their full string form. e.g. 100 is written one hundred. This is because numbers can be pronounced in different ways, e.g. one thousand five hundred and fifteen hundred. [There are libraries to convert number words to numbers](https://pypi.org/project/word2number/)
- Sentences are capitalized. Proper nouns are capitalized.
- Commas and other punctuation is used appropriately and sometimes ambiguously.
