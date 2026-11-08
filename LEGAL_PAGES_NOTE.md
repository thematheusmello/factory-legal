# Legal pages note: Spice Shelf Sort and Origami Canal

Added 8 November 2026. Nothing has been committed or pushed.

## Files added

- `spice-shelf/index.html`
- `spice-shelf/privacy.html`
- `spice-shelf/terms.html`
- `spice-shelf/icon.png` (copy of `builds/spice-shelf/store-assets/icon.png`, 512×512)
- `origami-canal/index.html`
- `origami-canal/privacy.html`
- `origami-canal/terms.html`
- `origami-canal/icon.png` (copy of `builds/origami-canal/store-assets/icon-128.png`, 128×128, generated from `assets/icon.svg`)
- `LEGAL_PAGES_NOTE.md` (this file)

## File modified

- `index.html`: added "Spice Shelf Sort" and "Origami Canal" to the header nav and added one card each. This follows the same pattern used when Lantern Lift was added.

No files in `crate-cram/`, `lantern-lift/`, `contact-extractor/`, `table-export/`, `style.css` or `.nojekyll` were changed.

## How the pages were made

Each page is crate-cram's page with only game-specific text changed. Running `diff crate-cram/<page> <slug>/<page>` shows every change. The changes are:

- game name, `<title>` and meta description
- effective date
- header nav: all six products, as on the root index
- product-page description, from `STORE_LISTING.md`
- privacy "Save data" paragraph, from each game's `PRIVACY.md`, checked against `src/game/save.ts`

Everything else is identical to crate-cram, byte for byte. That includes the identity sentence, contact email, footer, terms sections 1–6 and the rights/CNPD paragraph.

## Points to review before publishing

1. **No address, tax, refund or 14-day withdrawal text.** crate-cram's pages contain none of these. Its identity is only "Matheus Mello, an individual developer based in Portugal", the email address, and "Matheus Mello, Portugal" in terms §6. That was copied verbatim and nothing was added. The withdrawal position is therefore the same as crate-cram's:
   - there are no purchases, so there is no withdrawal clause;
   - terms §4 and §5 keep mandatory consumer rights.

   Refund and withdrawal wording exists only in the paid Chrome extensions' terms (`table-export/`, `contact-extractor/`).
2. **Effective date** is 8 November 2026 on all four policy pages. crate-cram and Lantern Lift show 7 November 2026. Change it if you publish later.
3. **Origami Canal wording differs from the template in three places:**
   - The privacy intro calls it an "HTML5 one-tap skill game", not a puzzle game.
   - The Save data paragraph starts "To remember your progress" instead of "To let you continue", because the game does not save a run in progress.
   - One sentence was added, taken from its `PRIVACY.md`: the platform may receive the best score where supported, and the game may report errors or warnings without save or personal data. In code, both happen only on YouTube Playables.
4. **Spice Shelf Sort's YouTube build also sends error and warning signals** (`health.logError()` / `logWarning()` with no data attached). Crate Cram and Lantern Lift do the same. Its `PRIVACY.md` does not mention this, so its page doesn't either. Copy Origami Canal's sentence if you want the two pages to match. Spice Shelf Sort never sends scores.
5. **Rewarded ads:** terms §2 keeps "Optional rewarded ads give in-game help only." Both new games also offer a rewarded "double coins" or "double lotus" bonus. Earlier games offered only help, such as a second chance or a swap. If you want that covered explicitly, consider "in-game help or bonuses only".
6. **Icon size:** `spice-shelf/icon.png` is the 512×512 store icon copied as-is, about 122 KB. The other site icons are 128×128. All icons display at 64 px, so it looks the same, but you may want to downscale it to match.
7. **Navigation on existing pages:** the existing product pages were not edited, so their navs don't link to the two new games. The same happened when Lantern Lift was added.
8. **Draft source:** Origami Canal's `PRIVACY.md` is marked "Draft for publisher review" and has a publisher TODO. Both games' `PRIVACY.md` files say the publisher must give a privacy URL and contact in the portal metadata. Once pushed, the URLs should be:
   - https://thematheusmello.github.io/factory-legal/spice-shelf/privacy.html
   - https://thematheusmello.github.io/factory-legal/origami-canal/privacy.html
9. **Generator script:** `publish/.tools/legal_site.py` only knows GridGrab, ContactSift and Crate Cram. Re-running it would overwrite `index.html` and remove Lantern Lift and both new games.
