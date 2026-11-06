# Tablut

[![Versione](https://img.shields.io/badge/versione-1.1-blue)](#versioni)
[![Licenza: AGPL v3](https://img.shields.io/badge/licenza-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-222?logo=github)](#pubblicazione-su-github-pages)
[![HTML5](https://img.shields.io/badge/HTML5-single%20file-E34F26?logo=html5&logoColor=white)](index.html)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES2020-F7DF1E?logo=javascript&logoColor=black)](index.html)
[![Lingua](https://img.shields.io/badge/lingua-italiano%20%7C%20inglese-green)](#)

Versione per browser del tablut, la forma di hnefatafl descritta da Linneo in Lapponia nel 1732 e di cui si hanno le regole più complete. È una singola pagina HTML, senza build, senza dipendenze e senza installazione. Condivide l'architettura del Gioco Reale di Ur, del Senet e del Wari: motore di gioco separato dall'interfaccia, animazioni, audio sintetizzato, storia e regole illustrate. Il tablut non ha elementi casuali.

## Caratteristiche

- **Regole** ricostruite dal testo latino di Linneo (tavola 9×9, 25 pezzi, re al centro, castello, cattura tra due nemici, cattura contro il castello vuoto, regole speciali per la cattura del re, vittoria del re su qualsiasi casa del bordo, patta). Le aggiunte moderne (muove per primo l'attaccante, patta) e le interpretazioni sono elencate nel pannello «Regole, strategia, note e fonti».
- **Quattro insiemi di regole** selezionabili nelle impostazioni (valgono dalla partita successiva): *Linneo (standard)*, predefinito; *Angoli (Pilarski)*, con vittoria del re su un angolo, castello e angoli ostili e riservati al re, limite di 100 mosse; *Cittadelle (Bologna)*, con i quattro accampamenti e il castello come cittadelle, fuga solo su caselle di bordo che non siano angoli né accampamenti, perde chi non può muovere; *Bannerlord (semplificato)*, con il re catturato da due lati ovunque. Il confronto fra le fonti e le scelte fatte dove i testi sono ambigui sono nel pannello «Regole, strategia, note e fonti».
- **Avversario**: computer a tre livelli (facile, medio, difficile; il predefinito è medio) o due giocatori sullo stesso schermo. Si può giocare con gli attaccanti o con i difensori. Il computer usa una ricerca alfa-beta con valutazione ricavata dalla sezione di strategia del testo: vie libere del re verso il bordo (o l'angolo), mobilità del re, blocco degli attaccanti, materiale. Quando gioca i difensori ai livelli medio e difficile, negli insiemi Linneo e Bannerlord, usa la valutazione descritta da Pilarski, che nelle prove ha dato risultati migliori.
- **Tavola** in legno con bordi intrecciati e nodi d'ispirazione norrena, case di partenza bruciate, castello al centro, pedine con motivo a quadrifoglio inciso e re con runa dorata. Le decorazioni sono disegnate nel codice, non copiate da immagini.
- **Aiuti di gioco**: destinazioni possibili evidenziate (disattivabile), segnalazione delle vie libere del re (disattivabile), suggerimento, annulla mossa e proposta di patta (il computer accetta solo se ritiene la propria posizione peggiore).
- **Audio** sintetizzato con Web Audio: effetti sonori (attivi di default) e colonna sonora d'ispirazione norrena (disattivata di default): bordone, tamburo a cornice, lira ad arco, canto di gola e corno, in re dorico a 66 battiti al minuto. La scelta è salvata nel browser.
- **Regole illustrate**: 15 passi animati, dalla tavola alla strategia.
- **Tutorial: partita guidata**: il computer gioca contro il computer, ma la partita avanza solo a comando dell'utente (pulsante «Mossa successiva» o freccia destra; «Mossa precedente» o freccia sinistra per tornare indietro) e un fumetto sulla tavola spiega il perché di ogni mossa: catture, minacce, vie del re bloccate o aperte, cordoni, sacrifici, con le alternative che perdevano quando la ricerca lo mostra. La partita è etichettata per fase (apertura, medio gioco, finale). La scheda *Lezioni* contiene 15 situazioni particolari (aperture, medio gioco, finali, per i diversi insiemi di regole), ciascuna verificata dal motore all'apertura della lezione e riprodotta con gli stessi fumetti.
- **Verifica delle strategie**: le strategie delle fonti sono state provate con il motore; i numeri e i limiti delle prove sono nel pannello «Regole, strategia, note e fonti».
- **Storia**: sequenza a titoli cinematografici dal testo fornito (Lapponia, Linneo, traduzione del 1811, varianti, riscoperta del latino). Durante la storia lo schermo del cellulare resta acceso.
- **Lingua**: interfaccia in italiano e inglese, con selettore IT/EN nella pagina. L'italiano è la lingua predefinita; la scelta è salvata nel browser.
- Tema chiaro e scuro automatico, layout adattabile a schermi piccoli. Con «riduci movimento» attivo nel sistema operativo le animazioni sono disattivate.

## Regole in breve

Gli attaccanti (16) muovono per primi; i difensori hanno 8 pezzi e il re. I pezzi si muovono come una torre, senza saltare né fermarsi su altri pezzi. Nessun pezzo può fermarsi sul castello centrale (si può attraversarlo se è vuoto). Un pezzo è catturato se due nemici lo chiudono su lati opposti, oppure tra un nemico e il castello vuoto; il re fa coppia con i difensori. Il re è catturato da quattro attaccanti se è nel castello, da tre se è accanto al castello, da due su lati opposti altrove. Il re vince raggiungendo una casa qualsiasi del bordo. Patta per ripetizione di posizione, per impossibilità di muovere o per accordo.

## Interpretazioni e limiti

- **Attraversare il castello**: il testo vieta di fermarsi sul castello; il codice permette di attraversarlo quando è vuoto. È una lettura della regola 5 e della regola 4, non un'affermazione esplicita del testo.
- **Ripetizione**: la partita è patta quando una stessa posizione, con lo stesso giocatore di turno, compare per la seconda volta. È una scelta di implementazione.
- **Patta per accordo contro il computer**: accettata solo se la valutazione statica del computer è peggiore di quella della posizione iniziale di più di una soglia fissa; è un criterio euristico.
- **Computer**: il livello difficile è limitato a circa 1,1 secondi per mossa (misurato in Node: media circa 0,5 s, massimo circa 1,05 s), quindi non è un giocatore perfetto. L'ordine di forza dei livelli è stato verificato con partite simulate a nodi limitati e al massimo 200 mezze mosse per partita, con inizio alternato: medio contro facile 44 vittorie, 0 sconfitte, 6 partite non terminate su 50; difficile contro facile 19-0-1 su 20; difficile contro medio 30-5-5 su 40. Non è una misura di forza assoluta.
- **Audio**: i suoni sono generati proceduralmente e non sono stati ascoltati dall'autore del codice; il giudizio sul risultato musicale è lasciato all'ascolto. L'accostamento allo stile di «Vikings» è un'intenzione di timbri e atmosfera (bordone, tamburo a cornice, lira ad arco, canto), non una riproduzione di brani esistenti.

Il motore è stato verificato con 500 partite casuali complete (invarianti: 25 pezzi iniziali, nessun pezzo non re sul castello, conteggio dei pezzi catturati) e con 47 scenari di regole (movimento, cattura, partner del re, castello vuoto, cattura del re nei tre casi, regola 11, vittoria, patta).

## Avvio

Apri `index.html` in un browser moderno. La pagina carica da Google Fonts, se raggiungibile, i caratteri; senza, usa quelli di sistema.

## Pubblicazione su GitHub Pages

1. Copia `index.html` nella radice del repository.
2. In *Settings → Pages* scegli il branch (ad esempio `main`) e la cartella `/ (root)`.
3. La pagina sarà all'indirizzo `https://<utente>.github.io/<repository>/`.

## Versioni

| Versione | Contenuto |
|---|---|
| 1.0 | Prima versione: gioco completo con tre livelli di difficoltà, animazioni, audio, storia e regole illustrate, in italiano e inglese con selettore della lingua. |
| 1.1 | Nuovi insiemi di regole (Angoli, Cittadelle, Bannerlord), tutorial guidato computer contro computer con spiegazioni, situazioni particolari, verifica delle strategie. |

## Fonti

- Testo di storia, regole e strategia del tablut fornito dall'autore del progetto; le regole si basano sulla descrizione in latino di Carl Linnaeus (1732).
- Immagini d'ispirazione per la tavola fornite dall'autore del progetto.
- S. Pilarski, *Designing an Effective Tablut Artificial Intelligence*, McGill University (regole con vittoria all'angolo; valutazione euristica).
- A. De Filippo, A. Galassi, A. Soriani, G. Trisolini, F. Baldo, F. Chesani, P. Mello, M. Milano (2025), *Improving the Teaching of Artificial Intelligence Through Project-Based Learning on a Board Game*, Intelligenza Artificiale 19(1), 17-29, doi:10.1177/17248035241297789 (regole con cittadelle).
- Jubal, *The Tablut Grandmaster's Guide (Bannerlord)*, forum Exilian, 31 maggio 2020, <https://exilian.co.uk/forum/index.php?topic=6188.0> (guida a un videogioco, fonte non accademica).

## Licenza

Copyright © 2026 Alessandro Valli.

Questo programma è software libero: puoi ridistribuirlo e modificarlo secondo i termini della GNU Affero General Public License, versione 3 o successiva. Se fornisci una versione modificata come servizio in rete, devi renderne disponibile il codice sorgente agli utenti. Il programma è distribuito senza alcuna garanzia. Testo completo: [LICENSE](LICENSE) e <https://www.gnu.org/licenses/agpl-3.0.html>.
