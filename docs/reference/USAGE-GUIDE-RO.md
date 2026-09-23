# AgentFlow — Ghid practic de utilizare

Status: `NON-NORMATIVE REFERENCE`  
Compatibil cu: `AgentFlow 1.1.1`

Acest document explică **cum folosești** AgentFlow. Nu redefinește procesul, statusurile, token-urile sau regulile Core.

Pentru reguli normative folosește:

- `GOVERNANCE.md` — proces, faze/statusuri, approvals;
- `AGENTFLOW.md` — Development Analysis, ATC, Evidence, Review;
- `DELIVERY-LIFECYCLE.md` — DEV/TEST/PROD;
- `AI-EXECUTION-RULES.md` — reguli pentru agenți AI;
- `DOCUMENTATION-POLICY.md` — context și documentație;
- `KIT-MANIFEST.md` — inventarul canonic al kitului.

## 1. Pentru un proiect nou

1. Rulează `BOOTSTRAP-PROCEDURE.md`.
2. Alege `GREENFIELD` sau `EXISTING`.
3. Lasă bootstrap-ul read-only asupra aplicației și infrastructurii.
4. Generează:
   - `PROJECT-ADAPTER.md`;
   - `agentflow.config.yaml`;
   - `BOOTSTRAP-REPORT.md`.
5. Rezolvă valorile `UNKNOWN/DECIDE/BLOCKED`.
6. Activează AgentFlow numai după approval-ul cerut de Core și Project Adapter.

## 2. Pentru un proiect existent

Nu converti tot backlog-ul retroactiv.

În mod normal:

- work nou intră în `AGENTFLOW`;
- work deja material început poate rămâne temporar `LEGACY-ADAPTED`;
- upgrade-ul framework-ului se face separat de schimbările aplicației.

Vezi `ADOPTION-GUIDE.md` pentru strategia de adopție.

## 3. Înainte de fiecare sesiune

Citește doar:

1. work item-ul curent;
2. `AI-EXECUTION-RULES.md`;
3. codul/configurația afectată;
4. secțiunile canonice strict relevante.

Nu reconstrui proiectul din istoricul chatului dacă starea poate fi citită din artefactele proiectului.

## 4. Când ai o cerință nouă

Pornește din:

`templates/REQUIREMENT.md`

Cerința trebuie să aibă scope, out-of-scope și acceptance criteria suficient de verificabile.

Procesul și approval-ul Requirement-ului sunt definite exclusiv în `GOVERNANCE.md`.

## 5. Când ai nevoie de arhitectură

Folosește:

`templates/ARCHITECTURE-DECISION.md`

Trigger-ele și regula de escaladare sunt în `AGENTFLOW.md` și `GOVERNANCE.md`.

Nu implementa o schimbare materială de arhitectură înainte de decizia aprobată.

## 6. Pentru Development Analysis și implementare

Development Analysis este read-only față de produs/runtime.

Pentru execuție folosește:

`templates/AGENT-TASK-CONTRACT.md`

`templates/EXECUTABLE-TASK.md` este păstrat doar pentru compatibilitate și nu înlocuiește ATC-ul aprobat.

## 7. După implementare

Folosește:

- `templates/EVIDENCE-BUNDLE.md`;
- `templates/INDEPENDENT-REVIEW.md`.

Review-ul trebuie să indice exact candidate identity. Dacă implementarea se schimbă, review-ul anterior rămâne istoric și trebuie repetat pentru noul candidate.

Detaliile normative sunt în `AGENTFLOW.md`.

## 8. Release

Urmează exclusiv `DELIVERY-LIFECYCLE.md`.

Pentru release record:

`templates/RELEASE-RECORD.md`

Nu folosi acest ghid ca sursă alternativă pentru gate-uri sau secvența de release.

## 9. Upgrade de framework

Înainte de upgrade:

1. verifică `CHANGELOG.md`;
2. verifică `COMPATIBILITY.md`;
3. nu suprascrie Project Adapter-ul local;
4. identifică noile valori obligatorii;
5. adoptă upgrade-ul explicit în proiectul consumator;
6. validează local înainte de a considera upgrade-ul activ.

Un release nou în `AgentFlow_Framework` nu modifică automat niciun proiect consumator.

## 10. Dacă nu știi ce urmează

Nu ghici din chat.

Verifică:

- current work-item Phase/Status;
- `GOVERNANCE.md`;
- blocker-ul curent;
- următorul gate;
- artefactul/evidence-ul necesar.

Pentru continuitate între chaturi vezi `docs/PROJECT-CONTEXT-HANDOFF.md` și `docs/design/ORIGIN-AND-DESIGN-INTENT.md`.
