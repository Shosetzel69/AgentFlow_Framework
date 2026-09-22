# AgentFlow Independent Kit — Instrucțiuni de folosire

Versiune compatibilă: AgentFlow Independent Kit v1.1.0

## 1. Ce este kitul

AgentFlow este un framework de software delivery asistat de agenți AI.

Scopul lui este să controleze trecerea de la idee la producție prin:
- cerințe aprobate;
- gate-uri de arhitectură;
- Development Analysis;
- Agent Task Contracts (ATC);
- aprobare explicită înainte de implementare;
- Evidence Bundle;
- Independent Review;
- DEV -> TEST -> PROD pe un candidate imutabil;
- rollback și owner approval înainte de PROD.

Kitul este independent de un anumit repository, cloud provider, model AI sau sistem de CI/CD.

---

## 2. Ce fișier folosești

Pentru un proiect nou ai nevoie doar de kitul din acest repository.

Poți păstra AgentFlow:
- într-un folder dedicat în proiectul țintă;
- sau într-un repository separat și aplica framework-ul prin Project Adapter.

Fișierele individuale furnizate separat de un eventual ZIP sunt doar copii de conveniență. Repository-ul este sursa preferată.

---

## 3. Primul pas — alege modul de adopție

### GREENFIELD

Folosește acest mod dacă proiectul este nou și nu are proces de delivery existent.

Ținta este adoptarea directă a AgentFlow pentru toate work item-urile.

### EXISTING PROJECT

Folosește acest mod dacă proiectul are deja:
- cod;
- Issues;
- CI/CD;
- reguli de branching;
- documentație;
- work în desfășurare.

În acest caz:
- work nou poate intra în `AGENTFLOW`;
- work deja început poate rămâne temporar `LEGACY-ADAPTED`;
- nu se face conversie în masă fără analiză.

---

## 4. Rulează Bootstrap

Citește:

`BOOTSTRAP-PROCEDURE.md`

Bootstrap-ul trebuie executat inițial read-only față de produs și infrastructură.

Agentul trebuie să inspecteze proiectul și să producă:

```text
PROJECT-ADAPTER.md
agentflow.config.yaml
BOOTSTRAP-REPORT.md
```

Ordinea recomandată este:

```text
Preflight
-> Project Inventory
-> Source-of-Truth Map
-> Gap Analysis
-> Project Adapter
-> AgentFlow Config
-> Adoption Design
-> Validation
-> Owner Approval
```

Bootstrap-ul nu trebuie să modifice automat:
- codul aplicației;
- CI/CD;
- branch protection;
- secrete;
- baza de date;
- PROD.

---

## 5. Prompt minim pentru bootstrap

Poți folosi acest prompt într-un chat nou cu acces la repository:

```text
Aplică AgentFlow Independent Kit acestui proiect.

Urmează BOOTSTRAP-PROCEDURE.md.

Mod adopție: EXISTING PROJECT.

În această etapă lucrezi read-only asupra aplicației și infrastructurii.

Analizează repository-ul actual și produce:
1. Project Inventory
2. Source-of-Truth Map
3. Gap Analysis
4. PROJECT-ADAPTER.md
5. agentflow.config.yaml
6. BOOTSTRAP-REPORT.md
7. verdict READY_TO_ADOPT / READY_WITH_GAPS / BLOCKED

Nu modifica aplicația, CI/CD, infrastructura sau PROD fără un gate separat.
```

Pentru greenfield schimbă:

`Mod adopție: GREENFIELD.`

---

## 6. Verifică Bootstrap Report

Fișierul:

`BOOTSTRAP-REPORT.md`

trebuie să se încheie cu unul dintre:

### READY_TO_ADOPT

Framework-ul poate fi activat.

### READY_WITH_GAPS

Poate fi adoptat, dar există diferențe sau lipsuri care trebuie urmărite explicit.

Exemple:
- lipsă TEST separat;
- branch protection incomplet;
- rollback nedocumentat;
- documentație fără source-of-truth clar.

Aceste gaps nu trebuie ascunse.

### BLOCKED

Nu activa încă AgentFlow.

Trebuie întâi rezolvat blocker-ul indicat.

---

## 7. Configurează Project Adapter

`PROJECT-ADAPTER.md` este locul în care framework-ul generic este legat de proiectul concret.

Aici se definesc elemente precum:
- repository principal;
- issue tracker;
- branch principal;
- naming branch-uri;
- environments;
- CI engine;
- deploy mechanism;
- database/provider;
- test executors;
- AI agents;
- owner model;
- approval model;
- rollback mechanism;
- source-of-truth documents.

Nu modifica fișierele Core pentru a introduce detalii locale dacă acestea pot sta în Project Adapter.

---

## 8. Configurează agentflow.config.yaml

Pornește de la:

`agentflow.config.example.yaml`

și creează:

`agentflow.config.yaml`

Fișierul trebuie să conțină doar configurarea specifică proiectului.

Exemple:
- project name;
- adoption mode;
- owner;
- environments;
- branch rules;
- control tokens;
- enabled gates;
- adapters;
- repository metadata.

Nu pune secrete în acest fișier.

---

## 9. Fluxul normal de lucru

Pentru o funcționalitate nouă:

```text
IDEA
-> REQUIREMENT ANALYSIS
-> REQUIREMENT APPROVAL
-> ARCHITECTURE GATE, dacă este necesar
-> DEVELOPMENT ANALYSIS
-> READY FOR TASK CONTRACTS
-> AGENT TASK CONTRACT
-> APPROVE_TASK_CONTRACT <ref>
-> IMPLEMENTATION
-> EVIDENCE BUNDLE
-> INDEPENDENT REVIEW
-> DEV
-> CANDIDATE FREEZE
-> TEST
-> RELEASE READY
-> PROD_GO
-> PROD
-> SMOKE
-> DONE
```

---

## 10. Cerințe și Discovery

Folosește template-ul Requirement pentru a defini:
- problema;
- utilizatorul afectat;
- rezultatul dorit;
- scope;
- out of scope;
- acceptance criteria;
- invariants.

Discovery nu trebuie să prescrie implementarea tehnică.

După aprobare, cerința poate fi transferată spre Development Analysis.

---

## 11. Architecture Gate

Înainte de un ATC, verifică dacă taskul schimbă material:
- persistenta;
- source of truth;
- ownership-ul datelor;
- authentication;
- authorization;
- tenancy/multiuser;
- API comun;
- component boundaries;
- scheduler;
- concurrency;
- runtime/framework/provider;
- security/privacy;
- cost;
- portability.

Dacă da:

```text
STOP
-> Architecture
-> Decision
-> Owner Approval
-> Development Analysis revalidation
```

Nu implementa mai întâi și documenta ulterior.

---

## 12. Development Analysis

Development Analysis trebuie să fie read-only față de produs.

Trebuie să livreze:
- baseline verificat;
- impact;
- dependencies;
- architecture delta check;
- implementation slices;
- risks;
- Proposed ATCs;
- stop conditions;
- verdict.

Verdict normal:

`READY_FOR_TASK_CONTRACTS`

Development Analysis nu autorizează implementarea.

---

## 13. Agent Task Contract

Pentru fiecare unitate de execuție folosește template-ul:

`AGENT-TASK-CONTRACT.md`

Un ATC trebuie să conțină:
- ID;
- objective;
- scope;
- out of scope;
- dependencies;
- constraints;
- acceptance criteria;
- tests;
- retry limit;
- stop conditions;
- Evidence Bundle required.

ATC-ul trebuie să fie suficient de mic pentru review independent.

---

## 14. Aprobarea implementării

Implementarea începe numai după aprobarea explicită:

```text
APPROVE_TASK_CONTRACT <ATC-ref>
```

Exemple precum:
- ok;
- continua;
- merge;
- looks good;

nu trebuie tratate ca aprobare dacă procesul cere token explicit.

---

## 15. Implementarea

Executorul:
- implementează doar scope-ul ATC;
- nu schimbă arhitectura;
- nu extinde scope-ul;
- nu introduce dependințe materiale neaprobate;
- nu face refactor oportunist;
- respectă retry limit.

Dacă apare o decizie materială nouă:

```text
STOP
-> mark phase blocked
-> produce evidence
-> escalate to correct gate
```

---

## 16. Evidence Bundle

După implementare folosește:

`EVIDENCE-BUNDLE.md`

Include minimum:
- ATC;
- PR/SHA/candidate;
- files changed;
- tests și rezultate;
- mapping la Acceptance Criteria;
- assumptions;
- deviations;
- known limitations;
- residual risks;
- verdict.

Evidence Bundle trebuie să permită review-ul fără reconstruirea conversației.

---

## 17. Independent Review

Reviewerul compară:
- ATC aprobat;
- candidate-ul exact;
- Evidence Bundle.

Reviewerul nu modifică implementarea în același pas.

Verdicte:
- `REVIEW_PASS`
- `REVIEW_FAIL`
- `REVIEW_BLOCKED`

`REVIEW_BLOCKED` înseamnă că validarea nu poate fi terminată.
`REVIEW_FAIL` înseamnă că există dovadă că implementarea nu respectă contractul.

---

## 18. Candidate Freeze

După DEV PASS se fixează un candidate imutabil:

```text
CANDIDATE_SHA
```

Regula:

```text
DEV  = CANDIDATE_SHA
TEST = CANDIDATE_SHA
PROD = CANDIDATE_SHA
```

Orice modificare după freeze:
- invalidează candidate-ul;
- generează un SHA nou;
- reia DEV;
- reia TEST.

---

## 19. TEST

TEST validează candidate-ul exact.

Nu se repară direct în TEST.

Dacă TEST eșuează:

```text
TEST FAIL
-> DEV
-> fix
-> new candidate
-> DEV verification
-> TEST again
```

---

## 20. PROD

Înainte de PROD trebuie să existe:
- TEST PASS;
- candidate exact;
- previous known-good state;
- rollback cunoscut;
- owner approval.

Gate-ul recomandat:

```text
PROD_GO
```

PROD nu este mediu de debugging.

---

## 21. Rollback

Rollback-ul se pregătește înainte de deploy.

Pentru cod:
- previous known-good version;
- redeploy procedure.

Pentru config:
- previous config;
- restore procedure.

Pentru DB destructive change:
- backup;
- checksum;
- restore proof în non-PROD;
- rollback reference.

---

## 22. Documentația

Folosește cele patru niveluri:

### L0 — Handoff
Issues, PR-uri, release record.

### L1 — Canonical current state
Architecture, Governance, Requirements, contracts.

### L2 — Operational
Runbooks, migration procedures, QA procedures.

### L3 — History
Analize și documente superseded.

AI nu trebuie să încarce automat tot repository-ul.

Context implicit:
1. Issue/task curent;
2. AI execution rules;
3. cod/config afectat;
4. doar secțiunile canonice relevante.

---

## 23. Ce nu trebuie modificat în Core

În mod normal nu modifica:
- `GOVERNANCE.md`
- `AGENTFLOW.md`
- `DELIVERY-LIFECYCLE.md`
- `DOCUMENTATION-POLICY.md`
- `AI-EXECUTION-RULES.md`

pentru a introduce particularități ale proiectului.

Particularitățile se pun în:
- `PROJECT-ADAPTER.md`;
- `agentflow.config.yaml`.

Core se modifică doar când vrei să evoluezi framework-ul în sine.

---

## 24. Upgrade al kitului

La o versiune nouă AgentFlow:

1. compară Core vechi cu Core nou;
2. nu suprascrie direct Project Adapter;
3. păstrează configurația locală;
4. identifică breaking changes;
5. aplică update-ul controlat;
6. validează procesul înainte de utilizare.

Project Adapter și configurația proiectului sunt locale proiectului.

---

## 25. Structură recomandată în repository

```text
/agentflow
  GOVERNANCE.md
  AGENTFLOW.md
  DELIVERY-LIFECYCLE.md
  DOCUMENTATION-POLICY.md
  AI-EXECUTION-RULES.md
  FRAMEWORK-CONFIG.md
  BOOTSTRAP-PROCEDURE.md
  PROJECT-ADAPTER.md
  agentflow.config.yaml

  /templates
    REQUIREMENT.md
    DEVELOPMENT-TRANSFER.md
    ARCHITECTURE-DECISION.md
    AGENT-TASK-CONTRACT.md
    EVIDENCE-BUNDLE.md
    INDEPENDENT-REVIEW.md
    RELEASE-RECORD.md
    BOOTSTRAP-REPORT.md
```

Poți păstra kitul și într-un repository separat dacă preferi.

---

## 26. Regula practică de utilizare

Pentru proiect nou:

```text
Extract kit
-> Bootstrap read-only
-> Review Bootstrap Report
-> Complete Project Adapter
-> Complete config
-> Owner approves adoption
-> New work enters AgentFlow
```

Pentru fiecare feature:

```text
Requirement
-> Analysis
-> Architecture if needed
-> ATC
-> Explicit approval
-> Implement
-> Evidence
-> Review
-> DEV
-> TEST
-> PROD
```

---

## 27. Regula de bază

Dacă nu știi ce urmează, verifică:

```text
What Phase am I in?
What is the canonical Status?
What gate must be satisfied next?
Who owns that gate?
What evidence is required?
```

Dacă răspunsul nu este clar, nu continua automat la etapa următoare.

---

## 28. Principiile AgentFlow în 6 propoziții

1. Decide before coding.
2. Contract before execution.
3. Stop on material uncertainty.
4. Prove what was executed.
5. Review independently.
6. Promote one immutable candidate.
