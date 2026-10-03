# SUBTLEX-UK Explorer v1.0.0

The first release: an interactive page for exploring word frequency in British English, built on the SUBTLEX-UK dataset (160,022 words from British TV subtitles).

**Try it:** <https://gjdragon.github.io/subtlex-uk-explorer/>

## Highlights

- **Five linked charts.** Zipf score distribution (with a bin size you set), word length, part of speech, a rank-frequency curve, and contextual diversity vs. frequency.
- **Filters that update everything at once.** Top N most frequent words, word length, Zipf range, minimum CD, spelling search (contains, starts with, ends with) and part-of-speech toggles.
- **Click to drill down.** Click a bar in the word length or part-of-speech chart to filter to it.
- **Word table.** Sortable and paged, with rank, Zipf, CD, part of speech and lemma for each match.
- **One file, no server.** The data is built into `index.html`, which also follows your light or dark system theme.
- **MIT licensed** code.

## Good to know

- Words are ranked by Zipf score, with ties broken by contextual diversity. The source CSV is ordered by word length, so its row order is not a frequency rank.
- Proper names are about 39% of the list. Use the "No names" preset to focus on ordinary vocabulary.
- Needs a current browser (Chrome and Edge 80+, Firefox 113+, Safari 16.4+) and an internet connection on first load for Chart.js and fonts.

## Known limitations

- Part of speech is the dominant tag per spelling only.
- The CD vs. Zipf scatter plot shows a sample of up to 2,500 words.
- No CSV export of filtered results yet.

## Data and credit

Word frequencies come from SUBTLEX-UK: van Heuven, W. J. B., Mandera, P., Keuleers, E., & Brysbaert, M. (2014). SUBTLEX-UK: A new and improved word frequency database for British English. *Quarterly Journal of Experimental Psychology, 67*(6), 1176-1190.

The MIT license covers the code only. The dataset keeps its original terms.

Full changelog: see [CHANGELOG.md](CHANGELOG.md).
