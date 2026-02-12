# S-ON — Selection-Optimised Naming (BEM Adjacent)

**S-ON** is a **class naming methodology** (a convention for CSS, HTML, and UI systems) designed around one practical developer advantage:

> **Every meaningful part of a class name is optimised for fast double-click selection and rapid DOM targeting.**

S-ON preserves the contextual clarity of BEM (Block → Element → Modifier), but tightens the grammar to make class names faster to scan, faster to select, and faster to work with in CSS, JavaScript, and browser devtools.

This is not a framework — it is a lightweight, enforceable naming standard.

---

## Why S-ON?

Traditional BEM is excellent for structure:

```css
.card__header-title--large
```

But it introduces common friction:

- multiple separators
- chained element levels
- fragmented text selection

S-ON solves this by enforcing:

- **minimal structural hyphens**
- **underscore-based descriptors**
- **selection-optimised tokens**

S-ON is BEM, engineered for speed.

---

## The Core USP: Selection-Optimised Tokens

S-ON uses underscores (`_`) intentionally because most editors treat them as part of the same word.

That means double-clicking selects complete semantic units:

```css
.card-header_title_large
```

Double-click highlights:

- `header_title_large`

Not broken fragments like:

- `header`
- `title`
- `large`

This makes S-ON especially effective when:

- writing selectors quickly
- querying the DOM in JavaScript
- scanning markup in devtools
- working in component-heavy codebases

---

## Naming Grammar (Non-Negotiable)

S-ON allows only these class structures:

### 1. Block

```css
block_name
```

A standalone component. Hyphens are forbidden inside block names.

---

### 2. Element

```css
block_name-element_name
```

Exactly one single hyphen separates block → element.  
`element_name` may contain underscores.

---

### 3. Block Modifier

```css
block_name--modifier_name
```

A variation or state applied to the block.

---

### 4. Element Modifier (Exception Only)

```css
block_name-element_name--modifier_name
```

Allowed only when absolutely required. Prefer block-level modifiers.

---

## Separator Semantics

S-ON uses separators with fixed meaning:

| Separator | Meaning |
|----------|---------|
| *(none)* | Block |
| `-`      | Block → Element |
| `--`     | Modifier attachment |
| `_`      | Descriptor concatenation (selection-friendly) |

---

## Constraints (Non-Negotiable)

- Never use BEM `__` separators  
- Never chain single hyphens (no `block-a-b`)  
- Tokens must not contain `-` — use `_` instead  
- Prefer block-level modifiers over element modifiers  

---

## Relationship to BEM

S-ON is explicitly **BEM Adjacent**:

| Concept | BEM | S-ON |
|--------|-----|------|
| Block | `.card` | `.card` |
| Element | `.card__header` | `.card-header` |
| Modifier | `.card--active` | `.card--active` |
| Deep elements | `.card__header__title` | `.card-header_title` |

S-ON keeps BEM’s ownership model, but removes element chaining and optimises for selection speed.

---

## Copilot Prompt Contract (S-ON — Updated)
```shell
This is the contract Copilot must follow when generating or refactoring class names in S-ON.

### Core rules

- **Block:** use underscores only  
  ```css
  block_name
  ```
  Hyphens are forbidden inside block names.

- **Element:** exactly one structural hyphen separates block → element  
  ```css
  block_name-element_name
  ```
  `element_name` may contain underscores.

- **Block modifier:**  
  ```css
  block_name--modifier_name
  ```

- **Element modifier (exception only):**  
  ```css
  block_name-element_name--modifier_name
  ```
  Use only when absolutely required. Prefer block-level modifiers.

---

### Separator semantics

- `-` (single hyphen): structural only, used exactly once for block → element  
- `--` (double hyphen): attaches modifiers  
- `_` (underscore): unlimited, concatenates descriptive tokens for selection-friendly units  

---

### Constraints (Non-negotiable)

- Never use BEM `__` separators  
- Never chain single hyphens (no `block-a-b`)  
- Tokens must not contain `-` — use `_` instead  
- Prefer block-level modifiers over element modifiers  

---

### Selection principle (USP)

Class tokens must remain easy to double-click/select in editors and devtools.  
Underscores preserve contiguous semantic units.

---

### Examples

#### Valid

- `card`
- `card_header`
- `card_header-title`
- `card--is_active`
- `card_header-title--large` *(element modifier, exception)*

#### Invalid

- `card__header` (uses `__`)
- `card-header-title` (chained elements)
- `card--is-active` (hyphen inside modifier token)
- `block-name` (block contains hyphen)

---

### Output requirement

Copilot must generate class names that strictly conform to S-ON grammar.  
No additional naming schemes may be introduced.
```
---

## License

MIT — use freely in any project.
