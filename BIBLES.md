# Bundled Bibles

One Protestant Bible per app language, all in the shape of `en.json`: 66 books in KJV order, KJV chapter and
verse numbering (so "Psalms 51:10" or "Malachi 4:1" shows the same verse in every language), and `""` where a
translation has no separate text for a KJV verse. Psalm titles sit at the start of verse 1, as in `en.json`.

Rebuild everything except `en.json` with `python3 -I tool/fetch_bibles.py`. The script records every
renumbering rule and text fix, and lists the empty verses.

| Lang | Translation | Year | Licence | Source | Attribution required |
|---|---|---|---|---|---|
| en | King James Version | 1769 | Public domain (Crown patent applies in the UK only) | (already in the repo) | None |
| de | Lutherbibel | 1912 | Public domain | https://ebible.org/deu1912/ | None |
| fr | Louis Segond | 1910 | Public domain | https://ebible.org/fraLSG/ | None |
| ar | Smith & Van Dyke (Van Dyck) | 1865 | Public domain | https://ebible.org/arb-vd/ | None |
| zh | Chinese Union Version (和合本), New Punctuation edition (新标点和合本), simplified script | 1919 | Public domain (according to eBible.org) | https://ebible.org/cmn-cu89s/ | None |
| hi | Indian Revised Version (IRV) Hindi | 2019 | CC BY-SA 4.0 | https://ebible.org/hin2017/ | "Indian Revised Version (IRV) Hindi, © 2017, 2018, 2019 Bridge Connectivity Solutions Pvt. Ltd., https://ebible.org/hin2017/, licensed CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Changed: footnotes and cross-references removed, verse numbering aligned to the KJV." |
| ta | Indian Revised Version (IRV) Tamil | 2019 | CC BY-SA 4.0 | https://ebible.org/tam2017/ | "Indian Revised Version (IRV) Tamil, © 2017, 2019 Bridge Connectivity Solutions Pvt. Ltd., https://ebible.org/tam2017/, licensed CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Changed: footnotes and cross-references removed, verse numbering aligned to the KJV." |
| ja | 文語訳: Meiji Version (明治元訳) OT and Taisho Revision (大正改訳) NT | 1887 / 1917 | Public domain | https://github.com/scrollmapper/bible_databases (`sources/ja/JapBungo`, from CrossWire module JapBungo) | None |
| ko | Korean Revised Version (개역한글) | 1961 | Public domain in Korea (term ended 2011). US status uncertain, see below | https://github.com/scrollmapper/bible_databases (`sources/ko/KorRV`, CrossWire module KorRV, text from Korean Wikisource) | None |
| ml | Indian Revised Version (IRV) Malayalam (eBible.org edition "BCS 2025") | 2019 | CC BY-SA 4.0 | https://ebible.org/mal/ | "Indian Revised Version (IRV) Malayalam, © 2017, 2019 Bridge Communication Systems (Bridge Connectivity Solutions Pvt. Ltd.), https://ebible.org/mal/, licensed CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Changed: footnotes and cross-references removed, verse numbering aligned to the KJV." |
| te | Indian Revised Version (IRV) Telugu | 2019 | CC BY-SA 4.0 | https://ebible.org/tel2017/ | "Indian Revised Version (IRV) Telugu, © 2017, 2019 Bridge Connectivity Solutions, https://ebible.org/tel2017/, licensed CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Changed: footnotes, cross-references and the Song of Songs speaker notes removed, verse numbering aligned to the KJV." |
| es | Reina-Valera | 1909 | Public domain | https://ebible.org/spaRV1909/ | None |
| pt | Bíblia Livre (BLIVRE), Almeida 1819 Textus Receptus revised | 2018 | CC BY 4.0 Brasil | https://ebible.org/porbr2018/ | "Bíblia Livre (BLIVRE), Copyright © Diego Santos, Mario Sérgio, e Marco Teles, http://sites.google.com/site/biblialivre/ - fevereiro de 2018. Licença Creative Commons Atribuição 4.0 Brasil (http://creativecommons.org/licenses/by/4.0/br/). From https://ebible.org/porbr2018/. Changed: footnotes removed, verse numbering aligned to the KJV." |
| sw | Biblia Takatifu: Swahili Unlocked Literal Bible (ULB) | 2019 | CC BY-SA 4.0 | https://ebible.org/swhulb/ | "Biblia Takatifu, Swahili Unlocked Literal Bible, © 2019 Door43 World Missions Community, https://ebible.org/swhulb/, licensed CC BY-SA 4.0 (https://creativecommons.org/licenses/by-sa/4.0/). Changed: verse numbering aligned to the KJV, book-name spacing and one stray asterisk (REV 20:15) fixed." |

## Notes and open decisions

- **CC BY-SA (hi, ta, ml, te, sw) and CC BY (pt):** the app shows the attribution text above in Settings, About.
  The packs are encrypted, and these licences forbid technical measures that stop reuse, so `build_packs.py` also
  publishes these Bibles unencrypted in the content repo's `bibles/` folder, under their own licences.
  Our changed files must also stay under CC BY-SA 4.0 (CC BY 4.0 for pt). That covers the Bible files
  only, not the app code.
- **zh:** every digital CUV we found, including CrossWire's "1919" ChiUns module, has the 1988 New Punctuation
  text. eBible.org and CrossWire both list it as public domain. The punctuation editors (the Hong Kong Bible
  Society / UBS) have sometimes claimed rights in that edition. In the New Punctuation edition, some verses
  (for example Matthew 18:11) appear only in footnotes, so they are empty here.
- **ja:** the Colloquial Version (口語訳, 1954/55) is out of copyright in Japan, but it is probably still under
  copyright in the US until about 2050 (US copyright restoration of foreign works, URAA). Japanese Wikisource
  has a pending deletion request on this point. So we use the older literary version instead.
- **ko:** 개역한글 has the same US question: it was still under copyright in Korea in 1996, so the US may
  protect it until about 2056. The other choices are the 1911 Korean Bible (public domain everywhere, but in
  archaic Korean; on eBible.org as `kor`, with one chapter missing) or a licence for 개역개정 from the Korean
  Bible Society.
- **CC BY-SA (ml, te, sw) and CC BY (pt):** the same applies: show the attribution text above in the app.
  `pt.json` is CC BY 4.0, so it needs credit but not share-alike.
- **sw:** a word-for-word translation, used instead of Neno: Bibilia Takatifu (Biblica, meaning-based). The
  Swahili Union Version (1952) is still under the Bible Societies' copyright. Psalm titles are a plain paragraph
  before verse 1 in this source; the script puts them at the start of verse 1. Three verses are empty because the
  source joins them into ranges or omits them: 1CH 6:79 (in 6:78), 1CH 8:18 (in 8:17), LUK 17:36.
- **es:** eBible.org's digital Reina-Valera 1909 forces the Spanish chapter breaks into the KJV's verse counts.
  It does this by joining the last two verses of a chapter. The script moves the verses back. The joined verses
  stay joined, so the second verse of each pair is `""`: NUM 13:33, NUM 30:16, 1SA 24:22, 2SA 20:26, 2CH 33:11,
  JOB 35:16, HOS 12:14, JON 2:10, ACT 19:41, 2CO 13:13. The largest case is Job 39:27, which holds the text of
  KJV Job 39:27 to 40:5, so JOB 39:28-30 and 40:1-5 are empty.
- **te:** 100 verses are empty because the IRV Telugu joins verses into ranges (for example Matthew 1:22-23).
  The text is on the first verse of each range.
- **id (Indonesian): not built.** We found no complete Protestant Bible in Indonesian that is free to
  redistribute. Terjemahan Baru and Terjemahan Lama belong to the Indonesian Bible Society (LAI). Alkitab Yang
  Terbuka (AYT, https://ebible.org/indayt/) is complete, but its licence is non-commercial (CC BY-NC-SA, or
  BY-ND as eBible.org states it). Terjemahan Sederhana Indonesia (https://ebible.org/ind/, CC BY-SA 4.0) has only
  the NT and 21 OT books. Alkitab Gratis untuk Semua (https://ebible.org/indags/, CC BY-SA 4.0) has only the NT.
  Someone needs to choose: ask YLSA for permission to use AYT, license TB from LAI, or ship the partial TSI.
