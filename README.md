# Sub suprafață – siguranța infrastructurii din România în date publice

**Below the Surface: Romanian infrastructure safety in public data (bridges, pipelines, NDT market).**

> *Ce nu se vede, se poate verifica.*

Starea podurilor, a rețelelor de gaze și a echipamentelor sub presiune din România este documentată în zeci de surse publice separate, dar rar privită ca întreg. Acest proiect le aduce într-o singură bază de date deschisă și reproductibilă, construită exclusiv din surse publice și gratuite:

1. **Starea activelor** – poduri, rețele de gaze, echipamente sub presiune.
2. **Efortul de verificare** – contracte publice de inspecție și expertiză tehnică (SICAP, TED).
3. **Piața care face inspecția** – firmele de control nedistructiv și testări tehnice (CAEN 7120).

Autor: inspector NDT cu 14 ani de experiență în oil & gas, petrochimie, energie și construcții (PCN Level II PAUT și TOFD).

## Ce arată datele și ce nu arată

- **Arată:** o imagine publică, citată și verificabilă a stării infrastructurii și a efortului de inspecție, pe sectoare și pe județe.
- **Nu arată:** dacă un anumit pod sau o anumită conductă este periculoasă și nici calitatea inspecțiilor efectuate. Asemenea concluzii cer expertize tehnice, nu date publice.

## Arhitectură (ELT)

```
Surse (CSV, API, web, PDF, cereri Legea 544/2001)
  → Python: extragere și încărcare brută
  → DuckDB: strat brut (raw)
  → dbt + SQL: staging → marts (schemă stea)
  → Power BI și ghiduri publicate
GitHub Actions actualizează datele săptămânal.
```

## Structura repo-ului

| Dosar | Conținut |
| --- | --- |
| `fise-surse/` | Fișa fiecărei surse: URL, format, licență, coloane, limitări |
| `prompts/` | Prompturile folosite pentru cercetarea surselor |
| `cereri-544/` | Cererile de informații publice adresate instituțiilor |
| `extragere/` | Scripturi Python de descărcare și încărcare |
| `date/` | Date locale (regenerate din scripturi, nu sunt versionate) |
| `dbt/` | Transformări SQL versionate și testate |
| `lectii/` | Ghiduri pas cu pas despre metodele folosite |

## Etape

- [x] Structura proiectului
- [ ] Inventarul și colectarea surselor
- [ ] Arhitectura datelor (ELT)
- [ ] Baza de date (DuckDB + dbt)
- [ ] Analize și dashboard
- [ ] Ghiduri publicate

## Unelte (toate gratuite)

Python · DuckDB · dbt Core · Git și GitHub Actions · Power BI Desktop · VS Code

## Licență

Cod sub licența MIT. Datele aparțin surselor citate în `fise-surse/`.
