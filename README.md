# Il dato produttivo aiuta a prevedere i consumi energetici? — pagina di presentazione

Repository "di presentazione" (GitHub Pages) della tesina del Corso di Perfezionamento in Tecnologie Digitali per Ambienti e Sistemi Intelligenti (A.A. 2025/2026), **Proposta 15**: *Sistema intelligente per la previsione dei consumi energetici in ambito industriale*.

Pagina web: https://unisalento-idalab-corsoperfez-25-26.github.io/perfez-2526-presentation-sergi/

## Il progetto e l'architettura

**Il progetto.** Il lavoro si chiede se aggiungere ai soli dati storici di consumo un dato produttivo migliori le previsioni. Confronta una versione **A** (solo storico) con una versione **B** (storico più feature produttiva) su due dataset pubblici (WWTP Melbourne e UCI Steel), con tre algoritmi (Ridge, Random Forest, Prophet) e tre orizzonti (breve, medio, lungo), cioè 18 combinazioni, con protocolli di validazione temporale, una previsione di riferimento (persistenza) e test statistici. Con il protocollo principale una sola combinazione mostra un beneficio rilevante (Random Forest su WWTP a lungo termine, −5,7%), che però dipende dal protocollo di validazione ed è al limite della significatività statistica.

**L'architettura.** Il sistema è progettato a sei livelli:

| Livello | Funzione | Stato |
|---|---|---|
| L1 | Acquisizione di consumi e dati operativi/produttivi (dataset o sensori IoT) | usa dataset pubblici; l'acquisizione con sensori IoT è solo progettata |
| L2 | Costruzione delle feature (calendario, ritardi, feature produttiva) | implementato |
| L3 | Modelli (Ridge, Random Forest, Prophet) | implementato |
| L4 | Previsioni a tre orizzonti | implementato |
| L5 | Validazione (cross-validation temporale, riferimento, test statistici, stabilità) | implementato |
| L6 | Supporto alle decisioni operative (pianificazione, budget, report) | solo progettato; la dashboard legge i risultati già calcolati e non lo sostituisce |

**I componenti e i loro repository.**

| Componente | Che cosa è | Repository |
|---|---|---|
| `perfez-2526-wwtp-forecasting-sergi` | L2–L5 sul caso principale (WWTP Melbourne) | https://github.com/UniSalento-IDALab-corsoPerfez-25-26/perfez-2526-wwtp-forecasting-sergi |
| `perfez-2526-steel-forecasting-sergi` | L2–L5 sul secondo caso (UCI Steel) | https://github.com/UniSalento-IDALab-corsoPerfez-25-26/perfez-2526-steel-forecasting-sergi |
| `perfez-2526-dashboard-sergi` | Dashboard interattiva: un solo file HTML, apribile offline | https://github.com/UniSalento-IDALab-corsoPerfez-25-26/perfez-2526-dashboard-sergi |
| `perfez-2526-presentation-sergi` | Pagina di presentazione del progetto (questo repository) | https://github.com/UniSalento-IDALab-corsoPerfez-25-26/perfez-2526-presentation-sergi |

## Il componente di questo repository

Una pagina web statica (GitHub Pages) che racconta il progetto in parole semplici, in sei capitoli: la domanda (A contro B, con l'esempio della benzina), i due impianti con i tre algoritmi e i tre orizzonti, i risultati (le tre condizioni del beneficio, l'imbuto 18 → 4 → 3 → 1 e le 18 combinazioni esplorabili), il risultato principale sotto esame (che cosa regge e che cosa vacilla), l'ipotesi della ridondanza con le indicazioni per un'azienda, e infine i sei livelli dell'architettura con i link ai repository. Contiene:

- `index.html`: la pagina (un solo file con stile e script incorporati; usa solo i font di Google). Le illustrazioni sono disegni esplicativi in SVG; tutti i grafici e i numeri provengono dai risultati della tesina. Gli elementi interattivi sono le 18 combinazioni (con il dettaglio di ciascuna) e l'imbuto delle tre condizioni; l'esplorazione per protocollo e per fold è nella dashboard;
- `assets/`: i loghi dell'Università del Salento e del Patto territoriale (Sistema universitario pugliese);
- `dashboard/index.html`: la dashboard interattiva, apribile direttamente dal sito;
- `documenti/`: la tesina in PDF;
- `.nojekyll`: indica a GitHub Pages di servire i file così come sono.

## Pubblicazione

In **Settings → Pages**: *Source* = "Deploy from a branch", branch `main`, cartella `/ (root)`.
