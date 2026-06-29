# Party20 Character Sheets + Beyond20 Bridge

Party20 is a small set of local/static HTML character sheets plus a modified Beyond20 browser extension. The sheets can send rolls, attacks, spell cards, trait cards, summon cards, and other table information to Roll20.

This build supports:

- **Brindle Duskhorn** — level 6 Satyr Wizard, Bladesinger
- **Tiny** — level 6 Halfling Barbarian
- **Thalia** — Wood Elf Fighter / Battle Master, including the level 6 sheet if you use the newer Thalia HTML
- **Lilothah Enakathil** — level 6 Drow Druid, Circle of the Shepherd
- Lilothah’s collapsible SRD creature cards
- Lilothah’s **Bestial Spirit** summon card with spell-level and form dropdowns
- Roll20-compatible buttons for checks, saves, initiative, attacks, damage, traits, spells, summons, and creature stat blocks

## Package contents

A complete package normally contains these folders:

```text
extension-chrome/      Modified Beyond20/Party20 extension for Chrome or Edge
extension-firefox/     Modified Beyond20/Party20 extension for Firefox
site/                  Character sheets and shared Party20 scripts/styles
README-Party20.md      This setup and use guide
```

The `site/` folder normally contains:

```text
index.html
party20-core.js
party20.css
brindle-duskhorn.html
brindle-duskhorn-standalone.html
tiny-halfling-barbarian.html
tiny-halfling-barbarian-standalone.html
thalia-wood-elf-fighter.html
thalia-wood-elf-fighter-standalone.html
lilothah-enakathil.html
lilothah-enakathil-standalone.html
```

The non-standalone sheets use the shared `party20-core.js` and `party20.css` files. The standalone sheets bundle everything into one HTML file and are convenient for copying or hosting individually.

## What needs to be open

For rolls to reach Roll20, keep these open at the same time:

1. A Roll20 game/campaign tab.
2. One Party20 character sheet tab, such as `http://localhost:8000/lilothah-enakathil.html`.
3. The Party20-modified Beyond20 extension installed and enabled.

Disable the normal Beyond20 extension while testing if you also have it installed, because running both may duplicate rolls.

## Running the sheets locally

Unzip the complete package, then open a terminal in the unzipped package folder.

```bash
cd site
python3 -m http.server 8000
```

Open this in your browser:

```text
http://localhost:8000/
```

You can then choose a character sheet from the index page, or open a sheet directly:

```text
http://localhost:8000/brindle-duskhorn.html
http://localhost:8000/tiny-halfling-barbarian.html
http://localhost:8000/thalia-wood-elf-fighter.html
http://localhost:8000/lilothah-enakathil.html
```

The extension is configured to work with local pages hosted at:

```text
http://localhost/*
http://127.0.0.1/*
```

## Hosting on GitHub Pages

You can also host the `site/` folder on GitHub Pages.

Recommended structure:

```text
https://anostus.github.io/party20/
```

or another path under:

```text
https://anostus.github.io/*
```

The extension is configured to inject the Party20 bridge on `https://anostus.github.io/*`, so GitHub Pages hosting should work as long as the files are published under that domain.

## Installing in Chrome or Edge

1. Unzip the complete package.
2. Open Chrome or Edge.
3. Go to:

   ```text
   chrome://extensions
   ```

   Edge users can use:

   ```text
   edge://extensions
   ```

4. Turn on **Developer mode**.
5. Click **Load unpacked**.
6. Select the unzipped `extension-chrome/` folder.
7. Confirm the extension appears as Party20/Beyond20 or the modified Beyond20 build.
8. Open Roll20 in one tab.
9. Open a Party20 sheet in another tab.
10. Click a roll button on the sheet.

Chrome and Edge load the extension from the folder you selected. If you move or delete that folder, the extension will stop loading until you load it again from its new location.

## Installing in Firefox

Firefox treats unpacked extensions as temporary unless you package/sign them separately.

1. Unzip the complete package.
2. Open Firefox.
3. Go to:

   ```text
   about:debugging#/runtime/this-firefox
   ```

4. Click **Load Temporary Add-on…**.
5. Open the `extension-firefox/` folder.
6. Select its `manifest.json` file.
7. Confirm the extension appears in the temporary extensions list.
8. Open Roll20 in one tab.
9. Open a Party20 sheet in another tab.
10. Click a roll button on the sheet.

Firefox temporary extensions are removed when Firefox fully closes. Reload the `manifest.json` after restarting Firefox.

## Using the sheets

Most interactive buttons are labeled with what they send to Roll20. Common buttons include:

- **Check** buttons for ability checks and skills.
- **Save** buttons for saving throws.
- **Initiative** buttons.
- **Attack** buttons that send attack rolls and damage.
- **Trait** buttons that send feature or rule text to chat.
- **Spell** buttons that send spell cards, healing, damage, or save information.
- **Stat/Traits** buttons that send monster or summon stat cards.
- **Multiattack** buttons that roll multiple attacks for summons/creatures when applicable.

The sheet status indicator usually shows whether the Party20 bridge is detected. If the sheet says the bridge is not connected, refresh the sheet and the Roll20 tab, then try again.

## Lilothah’s creature cards

Lilothah’s sheet includes collapsible cards for these SRD creatures:

- Brown Bear
- Giant Eagle
- Giant Spider
- Cave Bear, labeled as a Polar Bear SRD proxy if the SRD has no separate Cave Bear entry
- Giant Constrictor Snake
- Giant Elk
- Baboon
- Giant Badger
- Giant Owl
- Riding Horse
- Wolf
- Ape
- Crocodile
- Warhorse

Each creature card can be expanded/collapsed to keep the sheet compact. The cards include Roll20-compatible buttons for stats, traits, attacks, damage, and multiattacks where relevant.

Lilothah’s **Mighty Summoner** reminder is included on the summon/conjuration cards: beasts and fey summoned or created by Lilothah’s spells gain extra hit points per Hit Die and their natural weapon damage counts as magical. Check with the DM whether a given card is being used as a Wild Shape form, a conjured creature, or a normal reference creature.

## Lilothah’s Bestial Spirit dropdowns

Lilothah’s sheet also includes a collapsible **Bestial Spirit** card for *summon beast*.

Use the dropdowns before rolling:

1. Choose the **spell level** used to cast *summon beast*.
2. Choose the spirit form: **Land**, **Air**, or **Water**.
3. Click the roll buttons for:
   - Stat/trait card
   - Maul attack
   - Multiattack

The sheet updates Bestial Spirit values dynamically:

- **AC** = `11 + spell level`
- **HP** = base HP by form, plus scaling by spell level
- **Maul damage** = `1d8 + 4 + spell level`
- **Multiattack count** = half the spell level, rounded down
- Form-specific movement and traits update based on Land, Air, or Water

Bestial Spirit uses Lilothah’s druid spell attack bonus for Maul.

## Thalia level 6 note

A newer Thalia level 6 HTML sheet may be provided separately as:

```text
thalia_wood_elf_fighter_level6_party20.html
```

To use it from the site folder, either:

- Open it directly as a standalone HTML file, or
- Rename/copy it over `site/thalia-wood-elf-fighter.html`, or
- Add it to the site folder and link it from `index.html`.

The level 6 sheet updates Thalia’s Fighter features and roll math for the level-up. If you keep both level 5 and level 6 versions, make sure you open the correct file at the table.

## Common troubleshooting

### Rolls do not appear in Roll20

Check these first:

1. Roll20 is open in another tab.
2. The Party20-modified extension is enabled.
3. The original Beyond20 extension is disabled, or at least not duplicating/competing.
4. The sheet is hosted from a supported URL:
   - `http://localhost/*`
   - `http://127.0.0.1/*`
   - `https://anostus.github.io/*`
5. Refresh both the Roll20 tab and the character sheet tab.
6. Click the extension icon and confirm it is active for the current site if your browser asks for site permissions.

### The sheet opens but looks unstyled

For non-standalone files, make sure these files are in the same `site/` folder:

```text
party20-core.js
party20.css
```

A standalone HTML file should not require those shared files.

### Firefox loses the extension after restarting

That is normal for temporary add-ons. Go back to `about:debugging#/runtime/this-firefox` and load `extension-firefox/manifest.json` again.

### Chrome says the extension is from an unknown source

That is expected for an unpacked local extension. Keep Developer Mode enabled and load the `extension-chrome/` folder manually.

### Duplicate rolls appear

Disable the original Beyond20 extension or any older Party20/Brindle20 test build, then refresh Roll20 and the sheet.

### GitHub Pages does not work

Confirm the sheet URL begins with:

```text
https://anostus.github.io/
```

If you host under a different GitHub user or a custom domain, the extension manifest/content-script matches may need to be updated to include that domain.

## Updating or editing a character sheet

Most roll buttons are plain HTML buttons with embedded Party20 roll data. For small edits, search the HTML or character `.js` file for the character name, attack name, spell name, or trait name.

After editing:

1. Save the file.
2. Refresh the character sheet tab.
3. Test one simple roll, such as initiative or an ability check.
4. Test one attack or spell card.
5. Test Roll20 output before the game session.

## Session checklist

Before play:

1. Start the local server or open the hosted GitHub Pages site.
2. Open Roll20.
3. Load or enable the Party20 extension.
4. Open the needed sheet.
5. Make a test roll.
6. Confirm the result appears in Roll20 chat.
7. Collapse unused sections to keep the sheet easy to navigate.

