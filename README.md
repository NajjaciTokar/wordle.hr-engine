# wordle.hr engine

A chess-engine-style analysis tool for Croatian Wordle ([wordle.hr](https://wordle.hr)).
Enter the guesses from a game, set the tile colours, and the engine shows:

- how many candidate words remain and how much uncertainty is left (in bits)
- the best next guesses, ranked by expected information gain
- a game review that rates every move (Najbolji, Odličan, Dobar, Nepreciznost, Greška) and gives an accuracy score

It is a single static file (`index.html`) with no build step and no server. The interface is in Croatian.

## Use it

Open the GitHub Pages link for this repo, or just open `index.html` in a browser.

## First-time setup: load the word lists

This repo deliberately does **not** contain wordle.hr's word lists. They belong to the site, and the answer list is stored in
daily order, so publishing it would spoil every future puzzle. Each person loads the lists once in their own browser:

1. Open wordle.hr, press F12, go to the Network tab and reload the page.
2. Find the script named `main.<hash>.js`, open it in a new tab and save it (Ctrl+S).
3. In the tool, open **Popis riječi** and choose the saved file.

The tool extracts the word lists in your browser and remembers them for next time. The file is never uploaded anywhere.
When wordle.hr publishes a new script version, repeat the steps to refresh the lists.

## Using the engine

- Type a guess (`lj`, `nj` and `dž` are single tiles, as on wordle.hr) and press Dodaj.
- Click a tile to cycle grey, yellow, green so it matches what the game showed you.
- In Analiza, every word from both lists counts as a possible answer. In Igra, the secret word is drawn only from the first list (the real answer list).

## Igra and links

- **Igra** is a practice game with an on-screen keyboard (6 tries, secret word from the real answer list, no engine help). A game in progress survives a reload. When it ends, **Analiziraj** opens it in the Analiza tab.
- **Kopiraj poveznicu** (in the Analiza details) creates a link containing the whole game. Opening it asks for confirmation first, because it shows the words. Friends need the word lists loaded to see the analysis.

## Stablo

A study tool with two views. **Karta** (default) is an icicle map: pick an opening word and every colour outcome appears at once as a block whose height is the number of words left. Click a block to branch it, double-click to zoom in, drag to pan and use the wheel to zoom. The side panel shows alternatives, the remaining words and the guaranteed finish, and **Otvori u analizi** copies the path into the Analiza tab. **Lista** is a simpler step-by-step version of the same tree.

## Notes

Not affiliated with wordle.hr. Move ratings compare each guess with the best guess by information gain
(plus a small bonus for guesses that could be the answer), so they are a guide and not a full solver.
