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

## Notes and open decisions

- **CC BY-SA (hi, ta):** the app must show the attribution text above, for example on an About or Credits
  screen. Our changed `hi.json` and `ta.json` must also stay under CC BY-SA 4.0. That covers the Bible files
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
