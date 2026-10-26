# hadith translations

Per-book, per-language hadith translations for the hadith reader of the رفيق المسلم (Rafiq Al-Muslim) app.
Served from `https://raw.githubusercontent.com/mansourdxb/rafiq-al-muslim-assets/main/hadith_translations/...`
The app downloads a pack the first time a book is opened in a language that has one, and shows the
translation under the Arabic (falling back to the English of `hadith_combined/` for hadiths the pack doesn't cover).

## Format

`hadith_translations/<book>/<lang>.json` (compact JSON, `<lang>` = app language code):

```json
{"version":1,"book":"malik","lang":"ur",
 "source":{"edition":"urd-malik","dataset":"fawazahmed0/hadith-api","translator":"Waheed-uz-Zaman"},
 "count":1505,
 "items":{"<chapterId>:<idInBook>":"translation text", "...": "..."}}
```

- The item key is `${chapterId}:${idInBook}` of the hadith in `hadith_combined/<book>.json` (unique per book).
- `source.translator` is shown in the reader as the attribution line.

`hadith_translations/manifest.json` lists what exists:

```json
{"version":1,"books":{"malik":{"ur":{"count":1505,"bytes":1006278,"version":1}}}}
```

Bump a pack's `version` (in the file and the manifest) when its content changes.

## How packs are built

Each of our hadiths is matched to the [fawazahmed0/hadith-api](https://github.com/fawazahmed0/hadith-api)
`ara-<book>` edition by its Arabic text (normalised, Jaccard ≥ 0.6); the translation with the same source
`hadithnumber` is taken. Low matches, empty entries and length outliers are dropped. Arabic is never modified
and no text is generated. See `QC.md` for coverage, drop counts and samples.

## Sources and permission

The app owner has confirmed permission to use these translations. Attribution shown in the reader (`source.translator`):

| lang | books | translator / publisher |
|---|---|---|
| ur | bukhari | Muhammad Dawood Raz |
| ur | muslim | Darussalam (Muhammad Yahya Sultan Mahmood Jalalpuri) |
| ur | abudawud, tirmidhi, nasai, ibnmajah | Dar al-Da'wah, New Delhi |
| ur | malik | Waheed-uz-Zaman (public domain) |
| bn | bukhari | Tawheed Publication |
| bn | muslim, malik | Islamic Foundation Bangladesh |
| bn | abudawud, tirmidhi, nasai, ibnmajah | Unknown (not identified) |
| id | all | Lidwa Pusaka |
| ru | bukhari | isnad.link / Daura (Abdullah Nirsha) |
| tr | muslim | Ahmed Davudoğlu |
| tr | bukhari, abudawud, tirmidhi, ibnmajah, malik | Unknown (not identified) |

Not published: French (machine translation of the English), Russian Muslim/Abu Dawud (< 90% coverage),
Turkish Nasai (11% coverage); Ahmad and Darimi have no translations in the source.
