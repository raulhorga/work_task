# TaskFlow Control Center

Aplicație web statică pentru monitorizarea task-urilor personale, echipei și proiectelor, construită pornind de la arhitectura aplicației furnizate.

## Surse live EtherCalc

- Personale: https://calc.domainepublic.net/0y4rcf8ujgyf
- Echipă: https://calc.domainepublic.net/5wt3mqujqovw
- Proiecte: https://calc.domainepublic.net/if1566u5k4ly

Aplicația citește și scrie CSV prin endpoint-urile EtherCalc și sincronizează automat la 15 secunde. Dacă o foaie este goală, aplicația inițializează automat structura. Dacă o foaie conține deja date într-o structură necunoscută, aplicația NU o suprascrie.

## Funcții

- tab-uri Personale / Echipă / Proiecte;
- adăugare rapidă task, membru și proiect;
- membri inițiali: S.A, M.I, O.S, P.A, A.P;
- proiecte inițiale pe categorii:
  - Linii de Producție: SCA, SMT;
  - Proiecte Fabrică: IT Cost, FES, OT Cybersecurity, RoboTrainer;
  - Proiecte Globale: AutomaticBF, CRP;
  - Palantir: FPY, Hackathon, SMT Center;
- statusuri: Backlog, Open, In Progress, Waiting, Blocked, Delayed, Done, Cancelled;
- prioritate și progres 0–100%;
- data de start și deadline;
- owner și participanți;
- comentarii / update-uri săptămânale datate;
- istoric de modificări pentru trasabilitate;
- listă și Kanban;
- filtre și căutare;
- export Excel separat pentru categoria activă, inclusiv progress/comments;
- layout responsive pentru desktop, tabletă și mobil.

## Structura datelor

Fiecare foaie folosește un tabel cu `record_type`. Valorile pot fi `task`, `member` sau `project`. Comentariile și istoricul sunt păstrate în câmpuri JSON în aceeași înregistrare de task, pentru a păstra trasabilitatea completă în foaia aferentă.

## Rulare

Pune `index.html`, `styles.css` și `app.js` în același folder și publică folderul ca site static (GitHub Pages, server intern, Netlify etc.). Pentru test local este recomandat un server HTTP local, nu deschiderea directă prin `file://`.

Exemplu:

```bash
python -m http.server 8080
```

Apoi deschide `http://localhost:8080`.

## Notă CORS / rețea

Aplicația depinde de accesul din browser către `calc.domainepublic.net`. Dacă serverul sau politica rețelei companiei blochează CORS, este necesar un proxy intern / backend mic; interfața și modelul de date nu trebuie schimbate.
