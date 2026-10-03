# Changelog

All notable changes to SUBTLEX-UK Explorer are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the project uses [Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-10-03

First release. Live at <https://gjdragon.github.io/subtlex-uk-explorer/>.

### Added
- Interactive single-page explorer for the SUBTLEX-UK word frequency dataset (160,022 words).
- **Filters** that drive every chart, the summary stats and the word table together:
  - Top N most frequent words, with quick presets (100, 1,000, 5,000, 20,000, all).
  - Word length range.
  - Zipf score range.
  - Minimum contextual diversity (CD).
  - Spelling search: contains, starts with, or ends with.
  - Part-of-speech toggles, with presets for "All", "No names" and "Nouns, verbs, adjectives, adverbs".
  - Reset button for all filters.
- **Charts** (Chart.js):
  - Zipf score distribution with user-defined bin size and optional log scale.
  - Word length distribution, switchable between word count, share of words (%) and mean Zipf score.
  - Part-of-speech distribution with optional log scale.
  - Frequency curve: Zipf score against rank on a log rank axis.
  - CD vs. Zipf scatter plot (sampled to at most 2,500 points).
- Click-to-filter: clicking a bar in the word length chart or part-of-speech chart applies that value as a filter.
- Summary stats for the current selection: word count, share of the full list, mean and median Zipf, mean length, mean CD.
- Sortable, paged table (25 rows per page) showing rank, word, length, Zipf, CD, dominant part of speech and lemma.
- Light and dark themes that follow the system setting.
- Responsive layout, with the filter panel stacking above the charts on narrow screens.
- MIT license for the code.
- Hosted on GitHub Pages as a static site made of `index.html` and the source CSV, with no build step.

### Data handling
- Words are ranked by Zipf score (descending), with ties broken by CD. The source CSV is ordered by word length, so its row order is not a frequency rank.
- The words "nan", "none" and "null" are kept as words and not treated as missing values.
- The dataset is embedded in `index.html` as gzip-compressed, base64-encoded columns (about 1.2 MB), so the page makes no data requests and does not read the CSV at runtime.

### Known limitations
- Needs a browser with `DecompressionStream` support (Chrome and Edge 80+, Firefox 113+, Safari 16.4+).
- Chart.js and the Google Fonts stylesheet load from CDNs, so the page needs an internet connection on first load.
- Part of speech is the dominant tag for each spelling, so a word that is usually a noun but sometimes a verb appears only as a noun.
- The CD vs. Zipf scatter plot is a sample, not every matching word.
- No export of the filtered word list yet.

[1.0.0]: https://github.com/gjdragon/subtlex-uk-explorer/releases/tag/v1.0.0
