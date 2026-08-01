# Strona findgymbro.pl

Statyczna strona aplikacji. Żadnych zależności, żadnego procesu budowania —
zwykłe pliki, które wystarczy komuś wystawić.

```
index.html        opis aplikacji, zrzuty, miejsce na kod QR
prywatnosc.html   polityka prywatności, regulamin, kontakt
img/              zrzuty ekranu
favicon.png
```

Razem około 300 KB.

| Plik | Adres docelowy | Rola w App Store Connect |
|---|---|---|
| `index.html` | `findgymbro.pl` | — |
| `prywatnosc.html` | `findgymbro.pl/prywatnosc.html` | **Privacy Policy URL** i **Support URL** |

## GitHub Pages

Strona nie musi mieszkać w repozytorium aplikacji — wręcz nie powinna.
Osobne, małe repozytorium publiczne trzyma kod aplikacji przy sobie,
a stronę wystawia światu.

```bash
cd strona
git init -b main
git add .
git commit -m "Strona Find GymBro"
gh repo create findgymbro-strona --public --source=. --push
```

Potem w repozytorium: **Settings → Pages → Source: Deploy from a branch →
`main` / `root`**. Po chwili strona działa pod
`<login>.github.io/findgymbro-strona`.

**Własna domena:** w tym samym miejscu wpisz `findgymbro.pl` w polu
*Custom domain*. GitHub poda rekordy DNS do dodania w OVH
(**Domeny → findgymbro.pl → Strefa DNS**). Zaznacz *Enforce HTTPS* —
certyfikat GitHub wystawi sam, zwykle w kilkanaście minut.

> Repozytorium z GitHub Pages musi być publiczne, chyba że masz płatny plan.
> Dlatego trzymamy tu wyłącznie stronę: kilka plików HTML i trzy zrzuty
> ekranu. Kod aplikacji zostaje osobno.

## Cloudflare Pages — alternatywa

Jeśli wolisz nie zakładać publicznego repozytorium: `dash.cloudflare.com` →
**Workers & Pages** → **Create** → **Pages** → **Upload assets**, przeciągasz
zawartość tego katalogu. Domenę podpinasz w **Custom domains**.

## Aktualizacja treści

Pliki są generowane ze źródeł w katalogu roboczym sesji, nie pisane ręcznie.
Przy zmianach poproś o przebudowanie — ręczne poprawki zostaną nadpisane
przy następnej generacji.

Zrzuty ekranu są zmniejszone do 700 px szerokości. Oryginały w pełnej
rozdzielczości (1206×2622, wymagane przez App Store Connect) leżą
w `assets/zrzuty/`.

## Przed wysłaniem aplikacji do recenzji

Otwórz `findgymbro.pl/prywatnosc.html` **w trybie prywatnym przeglądarki**.
Treść bez logowania = recenzent Apple ją zobaczy. Niedziałający odnośnik do
polityki prywatności to jedna z najczęstszych przyczyn zwrotu aplikacji.
