# Mahabharata Family Tree

Interactive, self-contained family tree of the Mahabharata cast: **1633 people, 769 families/unions**
(includes 100 Kauravas, gods/apsaras where the epic treats them as parents, and 5 labelled placeholders).

- Data source of truth: `genealogy.py` (writes `data/mahabharata.json`)
- Template: `site_template.html` (adapted from the Ancestry tree UX, no Ancestry branding/analytics)
- Output: `site/index.html` (single file, open directly in a browser)

Parent links are typed: a child's *primary* family is the socially recognised one (e.g. Pandu + Kunti);
*secondary* links are labelled (divine father, biological (niyoga), foster, adoptive, born from fire).
Kinship search uses both kinds of links.

## Rebuild
    cd /workspace/mahabharata-tree
    python3 genealogy.py              # regenerate data/mahabharata.json
    python3 build_site.py             # writes site/index.html  (--noindex to add robots noindex, --home "Krishna" to change start person)
    /workspace/.venv-pw/bin/python tests/test_site.py   # Playwright checks + screenshots (uses /usr/bin/google-chrome; override with CHROME=...)

**Genealogy reference:** BORI Critical Edition of the Mahabharata (Pune), mainly Adi Parva chs. 57–63, 89–90, 94–117 and later parvas (Ganguli / van Buitenen translations); Harivamsha and the Bhagavata, Vishnu, Matsya, Vayu, Brahma, Brahmanda, Agni, Garuda, Padma, Kurma, Linga, Markandeya and Skanda Puranas (plus Valmiki Ramayana genealogies) for the creation lines (Svayambhuva Manu, Daksha, Kashyapa), the Solar dynasty (Ikshvaku to Rama and on to Brihadbala and Sumitra; Videha/Mithila), and the Lunar houses: Yadava (Haihaya, Kroshtu, Andhaka, Bhoja, Kukura, Vrishni; Krishna's 80 sons), Paurava and Kuru (both Adi Parva king-lists), Panchala, Magadha, Kashi, Anu (Shibi, Anga, Vanga, Kalinga), Druhyu and Turvasu. Where sources disagree, one reading is followed and the variants are noted on the person.

**Portraits:** major-character portraits are AI-generated illustrations in a consistent epic-painting style (not historical likenesses); others use initials placeholders.

Sources: Mahabharata Critical Edition (BORI) – Adi Parva 57–63, 89–90, 94–117 etc. (Ganguli / van Buitenen translations);
Harivamsha and Bhagavata Purana for Yadava links. Later-tradition items (Barbarika, Vrishaketu, Bhanumati, Lakshmanaa–Samba,
Shura's daughters) are flagged in notes.

## Parent roles
Each person carries `pr` = explicit parent list `[parent index|null, label, tag, primary]` built in `genealogy.py`
(`roles()`, with `ROLE_OVR` / `NO_MOTHER` for special cases). The Person panel shows a Parents card from it; the tree
captions every parent box (Legal father / Mother / Divine father / Foster …) and draws secondary parents with a dashed gold edge.

## Live site

https://vijaymd44-ops.github.io/mahabharata-tree/ (repo: https://github.com/vijaymd44-ops/mahabharata-tree)
