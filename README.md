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
- The dropdown under the file picker chooses which list counts as possible answers. The first list is the real answer list,
  so pick that one for the most accurate review. "Oba popisa" treats every accepted word as a possible answer.

## Publish with GitHub Pages

1. Create a new repository on GitHub and upload `index.html` and `README.md` (the `.gitignore` is optional).
2. Go to Settings, then Pages, set the source to the `main` branch and the `/ (root)` folder, and save.
3. Your page will be live at `https://<your-username>.github.io/<repo-name>/`.

## Notes

Not affiliated with wordle.hr. Move ratings compare each guess with the best guess by information gain
(plus a small bonus for guesses that could be the answer), so they are a guide and not a full solver.
