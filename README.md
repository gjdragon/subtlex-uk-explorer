# SUBTLEX-UK Explorer

An interactive, single-page explorer for the [SUBTLEX-UK](https://www.ugent.be/pp/experimentele-psychologie/en/research/documents/subtlexuk) word frequency dataset. Filter 160,022 British English words by frequency, length and part of speech, and see the distributions update live.

**Live site: <https://gjdragon.github.io/subtlex-uk-explorer/>**

Current version: **v1.0.0** (see [CHANGELOG.md](CHANGELOG.md)).

## What you can do

| Filter | What it does |
| --- | --- |
| Top N most frequent | Keep only the N highest-ranked words (presets: 100, 1,000, 5,000, 20,000, all) |
| Word length | Keep words between a minimum and maximum number of letters |
| Zipf score | Keep words within a Zipf range |
| Contextual diversity | Keep words whose CD is at least a chosen value |
| Spelling | Contains, starts with, or ends with a text fragment |
| Part of speech | Toggle categories, or use the presets "All", "No names", "Nouns, verbs, adjectives, adverbs" |

| Chart | What it shows |
| --- | --- |
| Zipf score distribution | Histogram with a bin size you choose, plus a log scale option |
| Word length | Word count, share of words or mean Zipf score by length. Click a bar to filter |
| Part of speech | Word count per category. Click a bar to filter |
| Frequency curve | Zipf score against rank on a log axis |
| CD vs. Zipf | Scatter of contextual diversity against frequency (sampled, up to 2,500 points) |

Below the charts, a sortable table lists the matching words with rank, length, Zipf, CD, part of speech and lemma, 25 per page.

## Key terms

- **Zipf score**: log10 of occurrences per million words, plus 3. Roughly, 1 to 3 is low frequency and 4 to 7 is high frequency.
- **CD (contextual diversity)**: the share of programmes in which the word appears, from 0 to 1.
- **Rank**: position when words are ordered by Zipf score (highest first), with ties broken by CD.
- **Part of speech**: the dominant tag for each spelling in the dataset.

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: page, styles, code and the word data. This is what GitHub Pages serves |
| `SUBTLEX-UK_selection.csv` | The source data, kept for reference. The page does not load it |
| `README.md`, `CHANGELOG.md`, `RELEASE_NOTES.md` | Documentation |
| `LICENSE` | MIT license |

There is no build step. The data in `index.html` is stored as compact, gzip-compressed columns and unpacked in the browser, so the page makes no data requests.

## Running it

- **Online:** open the live site above.
- **Locally:** download `index.html` and open it in a browser. It still needs an internet connection on first load, because Chart.js (cdnjs) and the Google Fonts stylesheet load from CDNs.
- **Your own copy:** fork the repository and turn on GitHub Pages for the main branch (Settings, then Pages).

Requirements: a browser with `DecompressionStream` support (Chrome and Edge 80+, Firefox 113+, Safari 16.4+).

## Data notes

- Words are ranked by Zipf score, because the CSV is ordered by word length rather than frequency.
- The words "nan", "none" and "null" are genuine entries. Some tools silently read them as missing values, so check this if you reload the CSV in your own analysis.
- Zipf and CD keep the three decimal places of the source.
- The embedded data in `index.html` was prepared from `SUBTLEX-UK_selection.csv`. If you edit the CSV, the page will not change.

## Known limitations

- Part of speech is one tag per spelling, so words that serve several roles show only their dominant one.
- The scatter plot is a sample of the matching words.
- No export of filtered results yet.

## Data source and credit

Word frequencies come from SUBTLEX-UK:

van Heuven, W. J. B., Mandera, P., Keuleers, E., & Brysbaert, M. (2014). SUBTLEX-UK: A new and improved word frequency database for British English. *Quarterly Journal of Experimental Psychology, 67*(6), 1176-1190.

## License

The code is released under the [MIT License](LICENSE). The SUBTLEX-UK dataset is not covered by it and keeps its original terms of use, so check them before redistributing the data.
