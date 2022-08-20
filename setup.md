# setting up anki

## install
- download and install anki from https://apps.ankiweb.net, got `2.1.54` for Apple Silicon

## account & sync
create an anki web account to sync and backup decks
- hit sync on desktop application, should prompt you to create an account
- create account on https://ankiweb.net/
- sync via desktop application

## creating notes
### note types
learn about note types, understand what fields will be necessary on the cards I want
- https://docs.ankiweb.net/getting-started.html#note-types
- https://docs.ankiweb.net/editing.html#adding-a-note-type

### prettify
[anki-prettify by pranavdeshai](https://github.com/pranavdeshai/anki-prettify)
- download `prettify.apkg` to install all the themes in one master deck
- in anki, Import File and select `prettify.apkg`
- new note type(s), THEME-NOTETYPE are created automatically
- cloned `prettify-minimal-basic_reverse` to create my card templates (one with a reverse and one with an optional reverse)

## add-ons
- [Minimal Theme](https://ankiweb.net/shared/info/867316254)
- [Migaku Anki Add-on](https://ankiweb.net/shared/info/1846879528)
- [Review Heatmap](https://ankiweb.net/shared/info/1771074083), color scheme: ice, calendar mode: continuous timeline

## debugging

### delete review history before a timestamp
from [this reddit comment](https://www.reddit.com/r/Anki/comments/d780ko/comment/f120bki/?utm_source=share&utm_medium=web2x&context=3)
- back up decks/collection
- cmd + shift + ; (opens debug console)
- paste code and replace millisecond timestamp
```
mw.col.db.execute("delete from revlog where id < 1660968000000")
mw.col.modSchema(False)
```
- cmd + enter (runs code)
- verify db history
- sync (upload) to anki web

### deleting a optional reverse card
from [this anki forum](https://forums.ankiweb.net/t/basic-and-optional-reverse-not-working-as-expected/9896)
- browse for card
- remove the text from the optional field
- Tools > Empty cards > Delete
