# sesu.dk — redesign

Statiske prototyper af ny forside og bordhøjde-landingsside for sesu.dk (Khaki ApS).
Ingen build, ingen afhængigheder. Ren HTML, CSS og vanilla JS.

## Indhold

| Fil | Rute | Hvad det er |
|---|---|---|
| `index.html` | `/` | Forside: formvælger, farver, produktgitter, inspiration |
| `bordhoejde/index.html` | `/bordhoejde/` | Beregner for bordhøjde med produktanbefaling og fragtmåler |

## Kør lokalt

```bash
python3 -m http.server 8080
# åbn http://localhost:8080
```

## Før produktion

1. **Produktdata.** `bordhoejde/index.html` indeholder et `PRODUCTS`-array med syv produkter,
   tastet manuelt ind fra sesu.dk. Det skal fyldes fra produktfeedet, så beregneren kan
   anbefale ben i alle højder. Felter: `form`, `h`, `name`, `finish`, `price`, `img`, `url`.
2. **Billeder.** Alle billeder hotlinkes fra `sesu.dk/wp-content/`. Skal pege på det nye
   CDN efter Shopify-migreringen.
3. **Kurv.** Knapperne "Læg i kurv" er attrapper. Skal kobles på cart-endpointet med
   korrekt antal (2 ben til A/U/X/trapez, 4 til hairpin og V).
4. **Anmeldelser.** Der er afsat plads under produktnavnet. Kræver rigtige data —
   sæt ikke stjerner ind, før de kommer fra Trustpilot eller Google.
5. **Fragtgrænse.** `FREE_SHIP = 1000` i `bordhoejde/index.html` skal matche shoppens
   faktiske grænse.

## Noter

- FAQ på bordhøjde-siden har `schema.org/FAQPage`-markup. Ret JSON-LD, hvis teksten ændres,
  ellers afviser Google det.
- `.nojekyll` er med, så GitHub Pages ikke forsøger at bygge siden.
