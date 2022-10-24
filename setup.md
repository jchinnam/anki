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

### [Review Heatmap](https://ankiweb.net/shared/info/1771074083)
- from widget Options, set color scheme: magenta
- from widget Options, set calendar mode: continuous timeline

### [Minimal Theme](https://ankiweb.net/shared/info/867316254)
- in add-on config, set `"remove editor button: audio recording": false` in order to make audio recording button available when creating cards, see [config](/add-ons/867316254_minimal_theme/config.json)

### [Migaku Anki Add-on](https://ankiweb.net/shared/info/1846879528)
- changed `Grading.button_color` response in `reviewer.py` to customize button text for `Good` and `Again` buttons, see [reviewer.py](/add-ons/1846879528_migaku/reviewer.py)

### [Large and Colorful Buttons](https://ankiweb.net/shared/info/1829090218)
- from add-on, view files and alter `user_bottom_buttons.css` to change `background-color` for `Good` and `Again` buttons, as well as `height`, `font-size`, and `margin` on all buttons; see [user_buttom_buttons.css](/add-ons/1829090218_large_and_colorful_buttons/user_bottom_buttons.css)

## troubleshooting

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
