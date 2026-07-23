# Script-specific realizations

The principles in SKILL.md are language-independent; only the symbol dialect
changes per writing system. Pick the column your audience reads natively —
a dialect is instant for insiders and opaque for everyone else.

| Principle | Latin / ASCII | Japanese / CJK | Caseless scripts (Arabic, Hebrew, Thai, ...) |
| --- | --- | --- | --- |
| Section header | `Details:` short heading, or CAPS (`DETAILS`) | `▼ 見出し` | short heading + blank line; CAPS does not exist |
| Key-value label | `Key: value` | `【キー】値` | `key: value`; verify order under RTL rendering |
| Divider | `---` | `---` or short `───` | `---` |
| List | `-` / `1.` | `・` / `1.` | `-` / `1.`; test bidi — ASCII bullets + RTL text can reorder visually |
| Consequence | `->` | `→` | prefer words; arrow glyphs are direction-loaded in RTL |
| Status | `[x]` / `[ ]` | `[x]` / `[ ]` (or 済/未) | `[x]` / `[ ]` |
| Warning line | `WARNING:` / `NOTE:` | `NOTE:` or `注:`/`補足:` | local equivalent of `note:` |

## Japanese / CJK notes

- 【】 (lenticular brackets) and ▼ are the native label and header markers — instant
  for Japanese readers, opaque to everyone else. Use them only for a Japanese audience;
  for mixed audiences fall back to the ASCII column.
- Japanese has no spaces and no letter case, so line breaks and symbols carry the
  entire structural load. That is why this dialect is richer than the Latin one —
  not a reason to use more of it.
- 機種依存文字 (platform-dependent characters: circled numbers ①②, some box-drawing
  and units) can render as tofu on other platforms. Prefer plain digits `1.` `2.`.
- Unify variant notations within a message: full-width vs half-width digits, and
  date formats (2026年7月14日 vs 7/14 — pick one; mixed formats force the reader to
  infer which year "7/14" belongs to).
- Japan's text-mail/メルマガ culture has a large repertoire of 罫線・囲み枠
  (rule-line and box-frame decoration). Most of it is attention-seeking, not
  structural — the admission rule in SKILL.md deliberately takes only the
  structural subset (label, header, short divider) and leaves the rest.

## Accessibility notes (all scripts)

- Screen readers announce decorative characters one by one: a 20-character `───`
  divider is twenty announcements of "box drawings light horizontal". Prefer a
  blank line; if you must divide, `---` keeps the cost to three.
- `▼` is announced as "black down-pointing triangle" and visually mimics the
  near-universal "collapsed, tap to expand" UI affordance — a misleading signal.
  Use it sparingly and only as a section header.
- The structure that symbols encode visually is not conveyed aurally at all.
  Layer 1 (ordering, chunking, first-line conclusion) is the only layer that
  benefits every reader equally — one more reason it is the mandatory one.
