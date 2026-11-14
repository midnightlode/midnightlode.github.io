# Midnight Lode website

The studio's website: a home page, and a page and a privacy policy for each game. Plain HTML and one
stylesheet, no build step. Live at **https://midnightlode.github.io/** (GitHub Pages, branch `main`, root).
This file is not published (`_config.yml` excludes it).

## Files

| Path | What it is |
| --- | --- |
| `index.html` | Home: hero, each game (live games and coming-soon ones), contact. |
| `privacy.html` | Lists every game's privacy policy. Its address was once the combined policy; keep it as the list so old links still land. |
| `<game>/index.html` | The game's page. |
| `<game>/privacy.html` | The game's own privacy policy. One policy per game: a policy never mentions another game. |
| `style.css` | Every page's look. Colours and fonts are the tokens at the top. |
| `img/` | Pictures: `<short>-icon.png` (256-384 px), screenshots as JPG about 900-1400 px wide, `favicon.png` (64 px). |
| `_config.yml` | Tells GitHub Pages what not to publish (this file, `_tools/`, `.claude/`). |
| `_tools/serve.js` | Serves the folder on http://localhost:8765 to look before pushing. |

Pages in a game folder use `../` for `style.css`, `img/` and the home page.

## The games and where their facts come from

Never write a game's description, numbers or privacy facts from memory: take them from its project or store page.

| Game | Folder here | Project | Store | Status |
| --- | --- | --- | --- | --- |
| Tap Miner | `tap-miner/` | `C:\Users\abdul.rehman\Tap Minner` | https://play.google.com/store/apps/details?id=com.midnightlode.tapminner | Live |
| World Racing Tournament | `world-racing-tournament/` | `C:\Users\abdul.rehman\WorldRacingTournament` | none yet (package `com.midnightlode.worldracingtournament`) | Coming soon |
| Sikander: The Conqueror | `sikander-the-conqueror/` | `C:\Users\abdul.rehman\SikanderTheConqueror` | none yet (package `com.midnightlode.sikander`) | Coming soon |

**Tap Miner**
- **Privacy policy:** its project's `docs/privacy.html` is the source. `tap-miner/privacy.html` is that text **word for word**, in this site's look; only the page around it differs. When the project's policy changes, copy the new text here. Its name is spelt "Tap Minner" in the policy, as in the project; the store title is "Tap Miner". Change both copies together or neither.
- **Page text:** the Play Store description (`store/listing.md` in the project).
- **Icon:** `store/StoreIcon_512.png`. Its feature graphic says "TAP MINNER", so it is not used here.
- **Ads and data:** Unity Ads only (rewarded, optional), Unity IAP through Google Play (gem packs, VIP pass), asks for ad consent on first open, target audience 13+.

**World Racing Tournament**
- **Privacy policy:** written here; there is no copy in the project. It must match what the game does: the ad companies are in `Assets/Scripts/Ads.cs` and `levelPlay` in `Assets/Resources/Config/game.json` (Unity LevelPlay, Unity Ads, Google AdMob through LevelPlay; Google UMP asks for consent). The game also uses Unity Authentication, Cloud Save, Cloud Code, Remote Config, Multiplayer Services and Relay (online races: player names, cars and live positions are shown to other players), and Google Play Games sign-in. Anzu (billboard ads) was taken out on 2026-11-14 because it is not in the game; add it back only when it is. Since 2026-11-14 it no longer says "not released yet" (closed testing, then production). Change it whenever an ad network, analytics, purchases or consent change, and update the "Effective" date.
- **Page text and numbers:** that project's `CLAUDE.md` (cars, modes) and `GAME_PLAN.md`. The car and mode counts come from `cars.json` and `modes.json` in `Assets/Resources/Config` there, counting only entries without `"enabled": false`.
- **Pictures:** `Assets/Icons/icon.png`; shots from `Assets/Resources/Loading/`.
- **When it launches:** swap "Coming soon to Google Play" for a Google Play button (same as Tap Miner's) on the home and game page, and remove "not released yet" from its policy.

**Sikander: The Conqueror**
- **Privacy policy:** written here; the project has none yet (its in-game policy screen is a placeholder, `GameUi.PrivacyText`). It must match `Assets/Scripts/Shop.cs`: Unity Ads (rewarded and interstitial) and Unity IAP through Google Play (gem packs, piggy bank, Remove ads). It says the game is not released yet and promises an ad-consent question before release (the project has none yet). Target audience 13+ is assumed, not set in the project. Change it whenever an ad network, analytics, purchases or consent change, and update the "Effective" date.
- **Page text and numbers:** that project's `CLAUDE.md` (1,500 states, 190 countries, 8 campaigns and 118 chapters: Philip 10, Sikander 50, Seleucus 18, and Antiochus, Mithridates, Cleopatra, Ptolemy and Antigonus 8 each; its own "78 chapters" and "Three campaigns" lines are older). Its `Store/listing.md` and some `Store/screenshots` are older (10 chapters, "Test store" on the store screen), so use them with care.
- **Pictures:** `Store/icon_512.png` (since 2026-11-01 a painted Sikander, not the globe and crown), `Store/feature_1024x500.png` (a globe, no title), and screenshots from its `Shots/` folder (2026-11-01: `back_menu`, `lato_hud`, `back_campaign`, `back_briefing`; portrait, shown with `gallery portrait`; `Store/screenshots/` is older).
- **When it launches:** same as World Racing Tournament: a Google Play button for "Coming soon", and remove "not released yet" from its policy.

## Adding a new game

1. Make a `<game>/` folder (lower case, hyphens) with `index.html` and `privacy.html`. Copy Tap Miner's pair to start; change every `href`, title and description.
2. The privacy policy: if the game's project has one, copy it word for word (as Tap Miner's). If not, write one from what the project actually uses (ad SDKs, purchases, analytics, consent, target audience) and tell the owner it needs his reading.
3. Add its card to `index.html` under "More from Midnight Lode", with "Game page" and "Privacy policy" links, and a choice to `privacy.html`.
4. Add its icon to `img/` (resized, not the full-size file) and a row to the table above.
5. Look locally, push, and give the owner its privacy address for the Play Console:
   `https://midnightlode.github.io/<game>/privacy.html`.

## Looking and publishing

- **Look first:** `node _tools/serve.js . 8765`, or start "website" in the Browser pane (`.claude/launch.json`). Check at phone width (375 px) that nothing scrolls sideways and every link and picture loads.
- **Never push.** The owner always pushes this site himself (2026-11-05: "I will manage on my own always"). Leave changes ready and tell him which pages changed. GitHub rebuilds one to two minutes after his push.
- Commits here are signed **Midnight Lode / midnightlode@gmail.com** (set in this repository only, so the owner's work email stays off a public repository). Do not change it.
- The repository belongs to the `midnightlode` GitHub account; this computer pushes as `abdulrehmankhalid906`, a collaborator. A 403 on push means that access was removed.
- End commit messages with the Co-Authored-By line from the session.

## Rules

- Only facts that are true today. A feature or ad network that is planned, not built, is described as coming, never as done.
- Keep the owner's email (`midnightlode@gmail.com`) as plain, selectable text; no forms (GitHub Pages has nowhere to send them).
- No outside scripts or trackers. Fonts from Google Fonts only.
- **Later:** `app-ads.txt` goes at the root of this site when an ad network asks for it; the Play listings' developer website must then be `https://midnightlode.github.io/`.
