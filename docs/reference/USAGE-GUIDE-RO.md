# AgentFlow — Ghid practic de utilizare

Status: `NON-NORMATIVE REFERENCE`  
Compatibil cu: `AgentFlow 1.2.x`

Acest document explică **cum folosești** AgentFlow. Nu redefinește procesul, statusurile, token-urile sau regulile Core.

Sursele normative sunt:

- `GOVERNANCE.md`;
- `AGENTFLOW.md`;
- `DELIVERY-LIFECYCLE.md`;
- `AI-EXECUTION-RULES.md`;
- `ARTIFACT-TRACEABILITY.md`;
- `DOCUMENTATION-POLICY.md`.

## 1. Pentru un proiect nou

1. Rulează `BOOTSTRAP-PROCEDURE.md`.
2. Verifică precondițiile de aplicabilitate.
3. Generează Project Adapter, config și Bootstrap Report.
4. Configurează durable approval record, candidate identity și access boundaries.
5. Activează numai după approval-ul bootstrap înregistrat durabil.

## 2. Pentru un proiect existent

Nu converti tot backlog-ul retroactiv.

Work nou poate intra în AgentFlow; work material început poate rămâne temporar `LEGACY-ADAPTED`.

Upgrade-ul framework-ului este separat de modificările aplicației.

## 3. Pentru un feature

Folosește template-urile canonice, în funcție de faza curentă:

- Requirement;
- Architecture Decision, dacă apare trigger;
- Development Analysis;
- Agent Task Contract;
- Evidence Bundle;
- Independent Review;
- Candidate Manifest;
- Release Record.

Nu folosi `EXECUTABLE-TASK.md` ca autoritate; este deprecated.

## 4. Evidence și review

Pentru mandatory checks:

- `ATTESTED` nu este suficient;
- trebuie `ARTIFACT` sau `REPRODUCIBLE`.

Independent Review trebuie să respecte nivelul configurat în Project Adapter și să fie legat de exact candidate ID.

## 5. Release

Urmează exclusiv `DELIVERY-LIFECYCLE.md`.

Candidate Manifest este obligatoriu înainte de freeze.

Dacă rollback-ul nu este fezabil, folosește numai forward-fix path-ul explicit autorizat din lifecycle.

## 6. Continuitate între chaturi

Nu reconstrui starea din memorie dacă există artefacte canonice.

Verifică:

- Phase/Status;
- artifact IDs și parent links;
- approvals;
- exact candidate;
- Evidence/Review;
- blocker;
- următorul gate.

## 7. Upgrade de framework

Înainte de upgrade:

1. verifică `CHANGELOG.md`;
2. verifică `COMPATIBILITY.md`;
3. verifică `CORE-VERSION-MATRIX.md`;
4. păstrează valorile locale din Project Adapter;
5. completează noile câmpuri;
6. rulează revalidation;
7. activează upgrade-ul explicit în proiectul consumator.

Un release nou în `AgentFlow_Framework` nu modifică automat nicio aplicație.
