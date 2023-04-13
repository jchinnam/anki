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

## theme & colors
going for a clean minimalist look
- using [minimal theme add-on](/setup.md#minimal-themehttpsankiwebnetsharedinfo867316254) for dashboard buttons and clean UI
- [migaku add-on](/setup.md#migaku-anki-add-onhttpsankiwebnetsharedinfo1846879528) simplifies buttons down to only `again` and `good`
- using hex codes `#deb7c1` for again & `#d0eab7` for good across multiple add-ons

## add-ons

### [Review Heatmap](https://ankiweb.net/shared/info/1771074083)
- from widget Options, set color scheme: magenta
- from widget Options, set calendar mode: continuous timeline

### [Minimal Theme](https://ankiweb.net/shared/info/867316254)
- add-on > config: set `"remove editor button: audio recording": false` in order to make audio recording button available when creating cards, see [config](/add-ons/867316254_minimal_theme/config.json)

### [Migaku Anki Add-on](https://ankiweb.net/shared/info/1846879528)
- add-on > view files: changed `Grading.button_color` response in `reviewer.py` to customize button text for `Good` and `Again` buttons, see [reviewer.py](/add-ons/1846879528_migaku/reviewer.py)

### [Large and Colorful Buttons](https://ankiweb.net/shared/info/1829090218)
- add-on > view files: alter `user_bottom_buttons.css` to change `background-color` for `Good` and `Again` buttons, as well as `height`, `font-size`, and `margin` on all buttons; see [user_buttom_buttons.css](/add-ons/1829090218_large_and_colorful_buttons/user_bottom_buttons.css)

### [See Previous Card Ratings in Reviewer](https://ankiweb.net/shared/info/1906641654)
- add-on > config: change `vertical-position` to `top` and set colors for `rated-again-color` and `rated-good-color` to match my scheme, see [config](/add-ons/1906641654_previous_card_ratings/config.json)

### [Reset Ease Automatically](https://ankiweb.net/shared/info/12081346)
this will reset cards to 250 every time I review on desktop or Tools > Reset Ease > Reset Ease
- Tools > Reset Ease > Preferences: set lower and upper bound for deck to 250
- Note: Migaku > Reset Card Ease also sets all cards to 250 but has to be done manually
- Note: also considered [Reset Ease](https://ankiweb.net/shared/info/947935257), [Set Card Ease](https://ankiweb.net/shared/info/1387847178) but they have to be done manually
- Note: also considered [Auto Ease Factor](https://ankiweb.net/shared/info/1672712021) but unclear how that change the algorithm

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
