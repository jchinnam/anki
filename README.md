# anki
[`setup.md`](/setup.md) for installation and customization notes

## cards
the deck is made up of optional reverse cards, where the front is in english and the back is in telugu--**recall cards**; if the optional `Add Reverse` field is populated with any text, the card also produces a reverse card with the telugu side on the front and english on the back--**recognition cards**

see [`cards/`](/cards/) for note type html and css

#### adopting my deck
if I sent you my telugu deck and you're looking to convert it from english -> telugu (optional reverse) to telugu -> english (basic) follow these steps:
- sync your existing anki decks
- file > import deck
- notes > manage note types
- clone note type: add > select “english → telugu” type > clone > name “telugu → english”
- select “telugu → english” > "cards..."
- flip front and back by manually updating the html templates, then save
- select all cards in deck
- switch note type to "telugu → english"
- notes > manage note types
- select “telugu → english” > "cards..."
- select card type "card 2" > remove note type

## add-ons
see [`add-ons/`](/add-ons/) for changes to add-on configs and files, with explanations in [`setup.md#add-ons`](/setup.md#add-ons)
