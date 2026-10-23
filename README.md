# Finding Life — language packs

Encrypted language packs for the Finding Life app: each holds one language's Bible and all of the app's content
(stories, journeys, help topics, questions, church history and the Region timelines).

| Path | What |
|---|---|
| `manifest.json` | Every published pack: `version`, `file`, `size`, `sha256`. The app reads it to offer downloads and updates. |
| `packs/<lang>-<version>.pack` | One language. Downloaded once from `https://rufus-sam.github.io/finding-life-content/`, then the app works offline. |
| `BIBLES.md` | Each language's Bible translation, licence and required attribution. |
| `bibles/<lang>.json` | The openly licensed Bibles (CC BY-SA / CC BY), unencrypted, under their own licences. |

Built from the app repo with `python3 -I tool/build_packs.py`; don't edit files here by hand. English also ships
inside the app.

The Bibles are public domain except the Indian Revised Version in Hindi, Tamil, Malayalam and Telugu (CC BY-SA 4.0,
© Bridge Connectivity Solutions), the Swahili ULB (CC BY-SA 4.0, © Door43 World Missions Community) and the
Portuguese Bíblia Livre (CC BY 4.0 Brasil); see `BIBLES.md`. Those are also published unencrypted in `bibles/`. App content © Finding Life.
