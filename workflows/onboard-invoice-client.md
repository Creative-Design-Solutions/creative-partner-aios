# Workflow: Onboard Invoice Client

## Objective
Generate a fully branded, client-specific invoice generator from the white-label template. Output is a standalone HTML file the client (or Bryan) can open in any browser — no install required.

## Inputs required
Collect these before starting. Ask Bryan if anything is missing.

| Field | Example |
|---|---|
| Client business name | Wisdom Surgery Clinic |
| Owner / contact name | Dr Anna Raymond |
| Tagline | Oral & Maxillofacial Surgery |
| Address (city, state/region, country) | Brisbane, Queensland, Australia |
| Email | anna@wisdomsurgery.clinic |
| Website (optional) | wisdomsurgery.clinic |
| Logo file path or URL | /path/to/logo.png |
| Brand colors (hex) | primary, secondary, accent, bg, text, muted, line |
| Default currency | AUD |
| Payment methods | label, value/QR path, note for each |
| Default thank-you message | Thank you, [Name]. |

## Color guidance
If the client hasn't defined colors, derive them from their logo or website:
- **primary** — darkest brand color (used for sidebar background)
- **secondary** — mid-tone brand color (used for table headers, meta bar)
- **accent** — highlight color (used for gold-equivalent: totals, headings, rule)
- **bg** — lightest brand tint (used for alternating rows, party block)
- **text** — near-black body text
- **muted** — subdued text (descriptions, sub-labels)
- **line** — faint border color (use accent at ~18% opacity)

## Steps

### 1. Read the template
Read `billing/invoice-generator-template.html` in full.

### 2. Encode the logo
```python
import base64
with open('/path/to/logo.png', 'rb') as f:
    b64 = base64.b64encode(f.read()).decode()
logo_uri = f'data:image/png;base64,{b64}'
```
Use `image/svg+xml` for SVGs, `image/png` or `image/jpeg` for raster files.

### 3. Encode QR codes (if any)
Same process as logo. One per payment method that has a QR.

### 4. Build the CLIENT config block
Replace every `{{PLACEHOLDER}}` in the template with real values:

```js
const CLIENT = {
  business:     "Wisdom Surgery Clinic",
  ownerName:    "Dr Anna Raymond",
  tagline:      "Oral & Maxillofacial Surgery",
  address:      "Brisbane, Queensland, Australia",
  email:        "anna@wisdomsurgery.clinic",
  website:      "wisdomsurgery.clinic",
  logo:         "<base64 data URI>",

  colors: {
    primary:   "#0a2540",
    secondary: "#1a56a0",
    accent:    "#2ab4b4",
    bg:        "#f0f8f8",
    text:      "#0f2a3d",
    muted:     "#5a7a8a",
    line:      "rgba(42,180,180,0.18)",
  },

  paymentMethods: [
    { label: "Bank Transfer", value: "BSB 123-456 · Acct 789012", note: "2–3 business days." },
    { label: "Wise", qr: "<base64 data URI>", note: "Best rate for USD → AUD." },
  ],

  defaultCurrency: "AUD",
  defaultThankyou: "Thank you, Anna.",
};
```

### 5. Write the output file
Save as `billing/clients/[slug]-invoice-generator.html`
where slug = lowercased, hyphenated business name (e.g. `wisdom-surgery-clinic`)

### 6. Copy to Desktop for Bryan
```bash
cp "billing/clients/[slug]-invoice-generator.html" ~/Desktop/
```

### 7. Commit
```
Add [Client Name] invoice generator
```

## Output
- `billing/clients/[slug]-invoice-generator.html` — branded, standalone, ready to use
- Committed to AIS-OS repo

## Notes
- The template file itself (`invoice-generator-template.html`) is never modified — always work from a copy
- If a client has no QR codes, omit the `qr` key from their payment method object
- If a client operates in multiple currencies, set `defaultCurrency` to their most common and they can switch in the app
- Each exported invoice filename auto-generates as `[inv-number]-[client-slug].html`
