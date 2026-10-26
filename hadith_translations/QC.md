# Hadith translation packs — QC report

Source: [fawazahmed0/hadith-api](https://github.com/fawazahmed0/hadith-api) editions `<lang3>-<book>`.
Each of our hadiths (`hadith_combined/<book>.json`) is matched to the source by its **Arabic text** (normalised Arabic, rare-token index, Jaccard similarity; match ≥ 0.6 required), then the translation with the same source `hadithnumber` is taken.
Drop reasons: `low_match` (no Arabic match ≥ 0.6), `empty` (source has no translation for that hadith), `length_outlier` (translation/Arabic length ratio > 3× or < ⅓ of the book×language median).
Only packs with a cleared licence are published here (currently Muwatta Malik in Urdu, translation by Waheed-uz-Zaman, public domain).

| book | lang | our hadiths | kept | coverage | low_match | empty | length_outlier | status |
|---|---|---:|---:|---:|---:|---:|---:|---|
| malik | ur | 1985 | 1505 | 75.8% | 158 | 253 | 69 | published |

## Cleaning

- Whitespace trimmed/collapsed, soft hyphens removed.
- Bare footnote markers like `[1]` / `[১]` removed (the footnote bodies are not in the dataset).
- Arabic is never modified; no text is generated.

## Samples (3 random)

### malik / ur
- `36:8` — AR: قَالَ يَحْيَى قَالَ مَالِكٌ عَنْ جَعْفَرِ بْنِ مُحَمَّدٍ، عَنْ أَبِيهِ، أَنَّ رَسُولَ اللَّهِ صلى ال…
  - UR: جعفر بن محمد اپنے باپ سے روایت ہے کہ رسول اللہ صلی اللہ علیہ وسلم نے فیصلہ کیا ایک قسم اور ایک گواہ پر ۔…
- `43:34` — AR: حَدَّثَنِي يَحْيَى، عَنْ مَالِكٍ، عَنِ ابْنِ شِهَابٍ، أَنَّ عُمَرَ بْنَ الْخَطَّابِ، نَشَدَ النَّاسَ…
  - UR: ابن شہاب سے روایت ہے کہ حضرت عمر رضی اللہ تعالیٰ عنہ نے بلایا لوگوں کو منی میں اور کہا کہ جس شخص کو دیت کا مسئلہ معلوم ہو وہ بیان کرے مجھ سے، تو ضحاک …
- `20:102` — AR: وَحَدَّثَنِي عَنْ مَالِكٍ، عَنْ نَافِعٍ، عَنْ عَبْدِ اللَّهِ بْنِ عُمَرَ، أَنَّهُ قَالَ حِينَ خَرَجَ…
  - UR: عبداللہ بن عمر جب نکلے مکہ کی طرف عمرہ کی نیت سے جس سال فساد درپیش تھا یعنی حجاج بن یوسف لڑنے کو آیا تھا عبداللہ بن زبیر سے جو حاکم تھے مکہ کے تو کہا …

