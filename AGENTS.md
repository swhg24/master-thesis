# Master Thesis Project Instructions

This repository supports Fuhan Liao's thesis at PEM, RWTH Aachen.

Thomas's supervisor-provided working title and the non-negotiable direction anchor are:

> **Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies**

This is the original working title supplied by Thomas and remains the non-negotiable direction anchor. The current thesis title, abstract, research questions, scope, and work packages are recorded separately in the 2026-09-18 registration materials and the 2026-09-20 checkpoint below. Every weekly case, evidence review, and candidate problem must remain traceably connected to **robotic systems in lithium-ion battery manufacturing**. A battery-equipment or material-flow description without a robotics question is not sufficient merely because it occurs inside a battery factory.

## Primary supervisor source and intended thesis profile

- **Research-direction precedence:** Thomas's latest explicit feedback -> `abschlussarbeiten_42444.pdf` -> internal guardrails -> weekly plans/case dossiers -> working hypotheses. For thesis direction and scope, lower-level project files must be revised when they conflict with a higher-level source; never reinterpret the PDF or Thomas's feedback merely to preserve an old candidate. Formal PEM/RWTH/ZPA rules remain authoritative for examination, registration, writing, submission, and colloquium matters.
- Treat `abschlussarbeiten_42444.pdf` (one page, authored by Thomas Fey) as the **highest original supervisor-provided research-direction source** for the title, initial situation, task profile, and intended breadth of the thesis.
- The PDF frames the work as an **analysis and evaluation of robotic systems along the battery cell production value chain**, not as a preselected robot-design or control-algorithm project.
- Its stated sequence is: overview current manufacturing processes and requirements -> identify suitable robotics applications -> assess selected applications technically and economically -> develop selected use cases into concrete application scenarios across cell formats and production environments -> outline future robotics trends and industrial implementation/research recommendations.
- The robotics categories explicitly named in the PDF are industrial robots, collaborative robots, and mobile systems. The typical applications explicitly named are material handling, automated inspection, flexible assembly, and intralogistics.
- The stated evaluation dimensions include automation potential, cost, quality impact, and scalability. The stated implementation challenges include delicate-material handling, integration, dry-room operation, and economic feasibility.
- Thomas's PDF also offers the student the option to shape the thematic focus. Therefore, the thesis may be an industry-forward, evidence-based technology and application assessment, and does not require every candidate to begin with a fully deployed industrial case. Prospective scenarios are allowed when the robotic actor, manufacturing task, technical rationale, comparison baseline, evidence boundary, and evaluation/evidence strategy are credible.
- The PDF does **not** explicitly name humanoid robots. The student's 2026-08-12 report that Thomas advised paying more attention to humanoids in the previous week's meeting is treated as current supervisor guidance reported by the student; preserve it as such until exact meeting wording or notes are available.
- Learning battery processes and process requirements is enabling work only. It must be used to derive, constrain, compare, or validate a robotic-system application; it must not become an independent equipment-description or process-optimization thesis path.

## Thesis type and intended contribution

- Treat the thesis as an **evidence-based prospective robotics application assessment in battery manufacturing**, not as a robotics algorithm, controller, foundation-model, hardware-development, or mandatory experiment/simulation thesis.
- The expected core is literature review + industrial cases + task and production-requirement analysis + robotic-system capability assessment + conditional application scenarios + implementation barriers/strategies + future potential.
- A new algorithm, robot design, codebase, physical demonstrator, large proprietary dataset, expert panel, or simulation is not a prerequisite for a valid thesis. Expert review, experiments, simulation, or quantitative analysis may be added only when they materially strengthen a defined claim and use transparent inputs.
- Review-oriented does not mean descriptive. The thesis must move beyond an application catalogue by applying a transparent, repeatable analysis method and producing evidence-bounded conditional conclusions about when different robotic-system architectures are suitable, unsuitable, or worth further evaluation.
- Use **credible evaluation / evidence strategy** rather than treating experimental validation access as a universal case-selection gate. Credibility may come from a traceable combination of peer-reviewed battery and robotics literature, industrial/equipment baselines, direct company disclosures, bounded cross-industry transfer, transparent engineering reasoning, and scenario-based assessment; expert review and simulation are optional enhancements.
- The current thesis route is **one deep reference case plus one to two evidence-sufficient adjacent battery-manufacturing applications**. Use the deep case to develop a reusable `Task -> Requirement -> Capability -> Suitability` assessment framework, then test and refine it through cross-case comparison. Do not increase the case count merely to cover every production level.

## Always apply

- Treat `docs/pem_thesis_requirements.md` as the project reference for PEM process, writing, citation, figure, submission, and colloquium requirements. Read the relevant section before advising on thesis structure, registration, writing, citations, figures, submission, or presentation.
- Treat `docs/collaboration_and_pacing.md` as the project reference for the six-month working rhythm, weekly planning format, GPT/Codex/student responsibilities, meeting-feedback loop, and Git handoff. Read it before proposing or executing a new weekly plan.
- Treat `docs/research_direction_guardrails.md` as the mandatory project reference for the thesis direction, current use case, robotics-relevance gate, scope boundaries, and candidate-decision rules. Read it before proposing a weekly plan, selecting or narrowing a case, changing a research question, or deciding that a technical detail belongs in the thesis.
- Distinguish clearly between: (1) official PEM/RWTH requirements, (2) supervisor guidance, (3) literature-supported findings, and (4) current working hypotheses. Never present a hypothesis as an official rule or established result.
- Preserve an evidence chain for research claims: claim -> source -> exact page/section when available -> implication for battery manufacturing -> implication for robotics.
- Do not invent cycle times, accuracy, yield improvements, costs, ROI, or maturity levels. Label missing evidence explicitly.
- Prefer peer-reviewed and recent international literature for the scientific argument. Industry and supplier sources may support implementation examples but must not substitute for academic evidence.
- Keep the thesis scope centered on lithium-ion battery manufacturing and always state whether evidence concerns cell, module, or pack production. The 2026-09-18 registration materials explicitly cover selected applications in cell, module, and pack manufacturing; this does not require the final case portfolio to contain one case from every level. Recycling remains adjacent unless Thomas explicitly broadens the boundary. Detailed robot-control algorithms remain outside the core unless the research question later requires them.
- Frame the research as: practical problem -> state of research/research gap -> evaluation or solution approach -> methodology -> validation -> conclusion and outlook.
- Keep editable source files for every thesis figure. Avoid screenshots and low-resolution scans.
- Before any formal registration, submission, or colloquium action, warn that bundled PEM documents include 2022/2025 versions and verify the latest templates, deadlines, examination regulations, and citation style with the supervisor/PEM/ZPA.
- Inspect the current week folders and working notes before proposing next steps; do not rely only on this file.
- Work at Master-Thesis scale and pace: one central learning question per week, with a minimum target and optional extension. Do not advance merely to fill Day 1–5 or make the project appear more sophisticated.
- Apply the rule **technical neutrality does not mean robotics neutrality**. Do not force AGV, AMR, robot arm, or humanoid into a case, but every potential thesis case must identify an actual or credibly evaluable robotic-system actor, the task or implementation decision being studied, and how a battery-manufacturing requirement changes that actor's role.
- Fixed conveyors, stacker cranes, inbound machines, dedicated transfer mechanisms, and process equipment may be reference architectures, comparators, or subsystems. They must not silently become the thesis core unless a genuine robotic-system problem, implementation decision, practical consequence, and credible evidence strategy are established and the scope is consistent with Thomas's intent.

## Thesis skill orchestration

The student does not need to name a Skill in ordinary requests. Infer the task type, select the smallest effective Skill set, announce the selected Skill(s) and purpose in a short commentary update, and then apply them. Do not invoke a Skill merely because it is installed. Normally use one primary Skill; add at most one complementary Skill when the task genuinely spans two distinct stages. For a larger end-to-end request, execute Skills sequentially and preserve the output of each stage instead of allowing overlapping workflows to compete.

Project authority always outranks third-party Skill defaults. Apply the research-direction precedence, PEM requirements, current case status, evidence rules, and weekly pacing in this file and the referenced project documents before following a Skill. A Skill's scoring rubric, paper genre, venue preference, prose convention, or workflow recommendation is advisory and must never silently redefine the thesis, manufacture a research gap, overrule Thomas, or replace missing evidence.

Use the following default routing:

- **Fast literature discovery, DOI/BibTeX, citation metadata, deduplication, or open-access status -> `academic-search`.** Prefer structured academic APIs. Do not start Chrome remote debugging or a CDP proxy, configure API keys, or download PDFs unless the task requires it and the user authorizes the relevant action. The installed upstream package references a legacy `check-deps.sh` that is not shipped; do not rely on that command.
- **Survey-grade investigation, evidence synthesis, closest-work search, counterexamples, or adversarial literature review -> `deep-research`.** Read the current case materials first, freeze the concrete research question, and require claim strength to match evidence strength. Do not also invoke the ARS deep-research route by default.
- **Title, research-question, case-selection, novelty, feasibility, or fatal-flaw assessment -> `idea-evaluator`.** Read `docs/research_direction_guardrails.md` and the current week/case notes first. Treat scores and verdicts as structured critique, not as a supervisor decision or proof of novelty.
- **Claim-citation audit, research-integrity check, structured manuscript review, or research-to-paper consistency audit -> `academic-research-suite`.** Prefer it for auditing an existing evidence set, while `deep-research` remains the default for building the evidence synthesis. Do not invoke cross-model transport, external providers, external-model upload, or experiment execution without explicit user consent.
- **A local paper/thesis logic skeleton or advisor-discussion structure -> `tech-paper-template`.** Adapt its technical-paper assumptions to a PEM engineering thesis; do not force a Technique/benchmark framing.
- **End-to-end cross-chapter story, material-to-chapter mapping, or complete manuscript build -> `paper-spine`.** Use only when the user requests whole-document orchestration or when the title/RQs, method, evidence base, and case status are sufficiently stable. Establish the output path and mutation scope before it writes files, and do not let it search for evidence merely to fill a predetermined story.
- **Drafting evidence-grounded prose -> `paper-writer`; Introduction-only drafting or restructuring -> `intro-drafter`.** Supply the approved outline and evidence pack. Do not create citations, performance values, costs, maturity claims, or conclusions beyond the supplied or verified evidence.
- **Language polishing -> `paper-polish` by default.** Use `nature-polishing` only when the user explicitly wants that style or its whole-manuscript academic-language discipline. Do not run both on the same passage by default, and preserve terminology, citation intent, uncertainty, and conditional claim strength.
- **Submission-stage adversarial review -> `pre-submission-reviewer`.** Use it for a mature full draft or when explicitly requested, not as the default reviewer for early weekly notes. PEM/Thomas requirements override its CS-paper, LaTeX, vocabulary, punctuation, or venue-specific preferences.
- **Figure logic and layout planning -> `figure-designer`; reconstruction of a supplied reference as an editable diagram -> `drawio-reconstruction`; data-driven scientific plots or multi-panel figures -> `nature-figure`.** Prefer editable Draw.io/SVG/PPT/vector sources for PEM thesis system diagrams. Do not use an external image-generation route or send data to OpenRouter without explicit consent.
- **Full-paper bilingual, figure/table/equation-aware reading -> `nature-reader`.** Use ordinary local reading for short extraction, a simple summary, or when the full bilingual reader would be disproportionate.
- **Formal Word thesis creation, audit, or formatting -> `thesis-docx`.** First read the relevant part of `docs/pem_thesis_requirements.md` and verify the current official PEM template/rules. This environment is Linux, so do not assume Word COM or PowerShell automation is available; prefer OOXML-compatible checks unless an appropriate Windows environment is explicitly provided.
- **`benchmark-paper-template` is not a default thesis Skill.** Use it only if the task genuinely concerns a benchmark/evaluation-paper contribution. **`vibe-research-workflow` is not a default research Skill.** Use it only for explicit questions about organizing an AI-assisted research workflow or choosing research tools.

For thesis questions, first classify the request as explanation, evidence search, deep synthesis, research decision, writing, review, figure work, or document production. Inspect the relevant current-week files and project references, choose the route above, and continue autonomously. For a new weekly plan, continue to follow `docs/collaboration_and_pacing.md`: one central learning question, a minimum target, and optional extension. If no installed Skill materially improves the task, work directly from the repository and evidence rather than forcing a Skill invocation.

## Current registration and research baseline (updated 2026-09-20)

Use the following precedence for the current thesis baseline:

1. Thomas's later explicit written or recorded feedback, if supplied;
2. `week_07_registration/Fuhan_Liao_PEM_Abstract_Full_Thomas_Review.pdf` and `week_07_registration/Fuhan_Liao_Erfassungsbogen_Masterarbeit_Thomas_Review.pdf`, both dated 2026-09-18;
3. the student's 2026-09-20 confirmation that the title, basic abstract, and research direction have been determined;
4. `docs/thesis_registration_consensus_2026-08-20.md` as the historical proposal and rationale record.

The research baseline is therefore treated as **fixed for current thesis work**, not as an open topic-selection exercise. However, do not claim that formal registration, topic issuance, or the official start/deadline has occurred unless a signed supervisor/professor/ZPA record or an explicit user update is available. The repository copy of the 2026-09-18 registration form still has the relevant administrative signature and ZPA fields blank.

The current thesis title is:

> **Task-Based Assessment of Robotic Systems in Battery Manufacturing: Application Potential and Implementation Strategies**

Current German title:

> **Aufgabenbasierte Bewertung von Robotersystemen in der Batteriefertigung: Anwendungspotenziale und Implementierungsstrategien**

The current research questions are:

1. **Which task and process characteristics determine the suitability of different robotic system architectures in selected battery manufacturing applications?**
2. **Under which technical, economic, quality, safety, and integration conditions are the considered robotic architectures suitable compared with dedicated automation and manual reference solutions?**
3. **Which implementation strategies and remaining research needs can be derived from the comparative case assessment?**

Preserve the following thesis logic unless a higher-authority source changes it:

```text
Battery-manufacturing task and industrial decision problem
-> task / process / production requirements
-> existing automation baseline
-> robotic-system capabilities
-> conditional architecture suitability
-> technical, economic and integration barriers
-> implementation strategies and future potential
```

The thesis is an **evidence-based comparative multiple-case assessment**. Its declared scope covers selected lithium-ion battery cell, module, and pack manufacturing applications. Battery-pack EoL test-connector handling is the detailed reference case, and one to two evidence-sufficient adjacent applications are used to assess and refine the framework. Week 06 provides a method prototype, not the final thesis contribution. Industrial robots, collaborative robots, mobile manipulators, and humanoid/mobile dual-arm systems are candidates to compare, not preferred answers; dedicated fixed-purpose automation and, where applicable, manual solutions remain reference architectures.

Always label the production level of each claim and case. The broad scope permits selection across cell, module, and pack manufacturing, but it does not justify combining evidence across levels without a transfer argument, nor does it require representative coverage of all three levels.

Do not mutate the title, RQs, or declared scope merely to fit new evidence, a new Skill template, or weekly-plan continuity. A change requires an explicit decision record triggered by Thomas's feedback, a defeated relevance/evidence gate, or a materially better and feasible thesis framing. When a higher-authority change occurs, update this checkpoint, `docs/thesis_registration_consensus_2026-08-20.md`, `docs/research_direction_guardrails.md`, and the active case plan together.

### Baseline change record

- **2026-08-20:** student–GPT–Codex registration proposal recorded; title/RQs/scope were still marked pending Thomas confirmation.
- **2026-09-18:** the latest abstract and Masterarbeit registration-form review copies recorded the current title, revised RQ1–RQ3, explicit cell/module/pack scope, Pack EoL detailed reference case, one to two adjacent applications, four work packages, and an 18-week plan.
- **2026-09-20:** the student confirmed that the title, basic abstract, and direction are determined. These are now the fixed internal research baseline. Formal signatures, ZPA registration, official start date, and deadline remain administratively unverified in the repository.

## Current research direction

- Week 01 established: battery fundamentals -> process requirements -> initial robotics opportunities.
- Week 02 established an evidence-based process/problem/robotics map, but supervisor feedback found the work too high-level and requested one step-by-step learning case.
- Week 03 completed the formation-aging-testing tray-transport learning cycle: process functions, conditional carrier flows, request/handover events, blocking/starvation, AGV control layers, and the evidence boundary of one rechargeable-battery AGV case. It produced a conditional conceptual model, not a confirmed factory layout.
- Week 04 completed a nearest-neighbor literature and counterexample audit. It showed that cell-finishing configuration research already includes some carrier functions, physical interfaces, and intralogistics transitions. Candidate A (operation-level carrier handover) and Candidate B (exception-triggered carrier flow) remain hypotheses, not established gaps.
- Week 05 uses one disclosed formation-loading architecture to fill an interface unknown from Week 03–04. Architecture B (`inbound machine 27 -> stacker crane 28 -> formation device 3`) is a **non-AGV fixed-automation reference/baseline**, not the thesis topic and not direct evidence for a robotic transport case.
- The Day 3 robotics-relevance audit found no direct evidence that a formation-specific condition changes the B2 stacker-crane task, and the fixed-automation interface does not by itself establish the robotics relevance intended by Thomas. B2 therefore remains a learning baseline/counterexample and exits the active thesis-candidate path; do not deepen it through further PLC, contact, positioning, or handover-state detail unless a new concrete robotic target case is supplied.
- Direction reset on 2026-08-12: return to Thomas's original industry-forward task profile and explore strongly robotics-related battery-manufacturing use cases. Give explicit attention to humanoid robots as requested in the student's report of the latest supervisor guidance, while comparing them against industrial robots, cobots, mobile robots, and dedicated automation rather than assuming that a humanoid form is advantageous.
- Current evidence indicates direct industrial humanoid deployments in battery module/pack manufacturing, including cell handling/loading and high-voltage testing, but no confirmed direct deployment in core battery-cell-manufacturing steps has yet been established. These deployments support application relevance; they do not independently prove performance, maturity, economic advantage, or general superiority.
- The A/B/C case-selection checkpoint has progressed: in the 2026-08-12 meeting Thomas accepted Pack EoL testing as a workable direction, and the student selected Candidate B for further study with Thomas's agreement. The 2026-09-18 registration materials now designate Pack EoL test-connector handling as the detailed reference case. It is not the thesis's only case and does not make CATL/Spirit AI the thesis object.
- Week 06 uses **battery-pack EoL test-connector handling** as the first deep reference case. DCR remains adjacent until evidence confirms that the same handling abstraction, connector, station, or robot applies. CATL/Spirit AI `Xiaomo` is an industrial anchor, not the object of the thesis and not independent proof of performance.
- Week 06 develops the first `Task -> Requirement -> Capability -> Suitability` framework by comparing dedicated automation, fixed industrial robots, and humanoid/mobile dual-arm systems. It must derive requirements from the manufacturing task before examining humanoid attributes and must produce conditional suitability rather than a brand ranking.
- Candidate A (cell identification, grasping, and loading) is the leading adjacent case to test framework transfer after Week 06; Candidate C (multi-station material handling and picking) remains a later option pending a concrete flow object and task boundary. Do not open all cases in parallel.
- The case charter records a stable analytical boundary and evidence minimum without turning the deep case into an immutable single-case thesis. Change the route only through an explicit decision record when supervisor direction changes, direct evidence defeats relevance, or a credible evidence strategy cannot support the intended claims.
- AGV fleet size/dispatching and robustness remain possible later directions, not current conclusions. Advance only if they answer a defined research question and process understanding, evidence, transparent inputs, and the evaluation strategy make them useful.

## Current project stage (2026-09-20)

The project is at the transition from **registration design completed** to **formal research execution beginning**. It is no longer in open-ended topic exploration, but it is not yet at the stage where thesis results or cross-case conclusions can be claimed.

### Completed or sufficiently stable

- The current English and German titles, abstract-level direction, three research questions, broad cell/module/pack scope, four work packages, and 18-week plan are recorded in the 2026-09-18 registration materials.
- Weeks 01–05 established battery-manufacturing fundamentals, a process/problem/task/robotics map, evidence-boundary discipline, nearest-neighbour and counterexample checking, and the exit of the formation stacker-crane path from the active thesis-candidate route.
- Week 06 established the Pack EoL test-connector handling case boundary and a first `Task -> Requirement -> Capability -> Suitability` method prototype (`F0`–`F7`, Task/Condition/Safety/Evidence gates).
- Pack EoL connector handling is the deep reference case. Candidate A, cell identification/grasping/loading in module/pack manufacturing, is the leading adjacent-case candidate. Candidate C remains exploratory and must not be opened in parallel without a failed Candidate A gate or a later explicit portfolio decision.

### Not yet completed; do not overstate

- Formal administrative registration, supervisor/professor signatures, the official start date, and submission deadline are not established by the repository copy currently available.
- The literature and case search is not yet systematic or reproducible. The repository has no complete bibliographic database or consolidated corpus for the Week 06 EoL, connector, flexible-cable, and robot-testing sources.
- Week 06 is a learning and method prototype, not an evidence-ready thesis chapter. Several class-level architecture claims, exact values, and illustrative scenario thresholds still require source-level verification, qualification as assumptions, or removal.
- The assessment dimensions have not yet been operationalized into explicit definitions, evidence requirements, and repeatable judgement rules. Do not create weighted scores without a defensible evidence basis.
- The final adjacent-case portfolio, cross-case synthesis, economic conclusions, implementation strategies, validation argument, Results, and Discussion remain open research work.
- Existing direct closest work on robotized lithium-ion battery testing must be audited before any novelty or research-gap claim. Do not claim that battery testing or connector attachment has not been studied.

## Persistent next-work sequence

Use this sequence as the default route after the registration baseline. It operationalizes the registered work packages; it does not replace the official 18-week plan. Complete the evidence and decision gates before advancing merely for schedule appearance.

### Step 0 — Baseline and repository synchronization

- Keep one canonical version of the current title, RQs, scope, case roles, and confirmation/registration status.
- Synchronize `docs/thesis_registration_consensus_2026-08-20.md`, `docs/research_direction_guardrails.md`, the active case plan, and this file when a confirmed decision changes.
- Preserve the editable source of the current abstract and registration text when available; do not treat a PDF-only review copy as the only long-term source.
- Keep administrative status distinct from research-direction status: a fixed research baseline does not by itself prove official ZPA registration.

### Step 1 — WP1 evidence protocol and structured evidence base

- Freeze the concrete evidence questions implied by RQ1–RQ3 before broad searching.
- Record databases, exact search strings, dates, inclusion/exclusion rules, deduplication, screening decisions, production level, and evidence type.
- Build a structured bibliography and evidence table with at least: claim ID; source; DOI/URL; exact page/section; cell/module/pack level; process; object; task; architecture; comparator; evaluation criterion; evidence class; supported conclusion; transfer limit; related RQ.
- Separate direct Pack EoL evidence, adjacent battery evidence, cross-industry transfer, company disclosure, and engineering inference. Claim strength must not exceed evidence strength.

### Step 2 — Pack EoL claim and closest-work audit

- Convert the Week 06 dossier into a claim-by-claim matrix.
- For each material statement, decide `retain`, `retain conditionally`, `downgrade to scenario/assumption`, or `remove`.
- Audit the nearest direct work on robotized lithium-ion/EV battery testing and connector handling before defining novelty or the research gap.
- Treat company success rates, speedups, scale, and deployment claims as company disclosures unless independently verified.

### Step 3 — Operationalize Framework v1.0

- Define each task characteristic, production requirement, robot capability, comparator, evaluation criterion, and suitability outcome.
- Replace technology-class stereotypes with configuration-specific questions. For example, assess whether the evaluated configuration actually has the required sensing, force/torque control, recovery logic, safety concept, and interface capability.
- Define explicit Task, Condition, Safety, and Evidence gate rules and how uncertainty is recorded.
- Prefer transparent conditional matrices and decision rules over a single score. Add weights only if their derivation and sensitivity can be defended.
- Establish the validation argument through traceability, within-case consistency, closest-work/counterexample checks, cross-case replication, and optional expert or sensitivity checks where they materially strengthen a defined claim.

### Step 4 — Adjacent-case gate, beginning with Candidate A

- Apply only `F0`–`F3` first: production level, source state, destination state, manipulated object, completion criterion, task boundary, battery-specific effect, comparator, and evidence sufficiency.
- Admit Candidate A to full analysis only if the robotics-relevance and evidence gates pass. If it fails, return to the candidate map; do not silently substitute Candidate C or open several cases at once.
- A broad cell/module/pack scope permits case selection across levels but does not require one case per level.

### Step 5 — Full adjacent-case application and cross-case synthesis

- Apply the same Framework v1.0 to the admitted adjacent case or cases.
- Compare recurring and case-specific task characteristics, requirements, capability bottlenecks, reference architectures, suitable conditions, failure conditions, and evidence gaps.
- Refine the framework only through documented changes; preserve what changed, why, and how it affects earlier case results.

### Step 6 — Implementation strategies and bounded technical/economic assessment

- Derive implementation strategies from the verified case results across technical, economic, quality, safety, scalability, and integration dimensions.
- Report missing quantitative inputs explicitly. Do not invent cycle time, utilization, defect reduction, investment, operating cost, ROI, or maturity rankings.
- Use scenarios or sensitivity analysis only with transparent assumptions and without presenting them as observed factory performance.

### Step 7 — Thesis drafting, integration, and quality assurance

- The Method skeleton may be drafted once the protocol and Framework v1.0 are stable. Results and Discussion claims must trace to the evidence matrix and completed case assessments.
- Maintain alignment among title, RQs, method, results, contribution claims, limitations, and recommendations.
- Complete citation verification, figure-source preservation, consistency review, language polishing, formatting checks, and current PEM/RWTH/ZPA rule verification before submission.

## Immediate next weekly cycle

Execution status reviewed on 2026-09-29:

- Baseline synchronization: **COMPLETE** across `AGENTS.md`, `docs/thesis_registration_consensus_2026-08-20.md`, `docs/research_direction_guardrails.md`, and the Week 06 active case plan.
- Evidence Protocol v1.0 and empty execution templates: **ESTABLISHED** in `week_08_evidence_protocol_pack_eol/`.
- Initial screening and claim audit: **IN PROGRESS — 34 screening records / 33 unique claims / 39 claim–source links** in `week_08_evidence_protocol_pack_eol/`. The second audit round removed universal prescriptions for dual arms/DLO estimation/F/T control and downgraded the exact safety and information topology to reference models. The 2026-09-28 public-source checkpoint (`14_public_source_checkpoint_2026-09-28.md`) adds direct Pack testing robot-design and dedicated-auto-contact patent precedents; these are design disclosures, not verified comparative deployment results.
- Full-text/official-full-HTML verification: **IN PROGRESS** for six core sources. S004 now supports only a bounded cross-industry flexible-harness mechanism claim; S018 establishes an adjacent battery-module requirements-to-work-cell precedent but not direct Pack EoL evidence; S006 still requires lawful institutional/author full text.
- Search execution: OpenAlex title searches and field-search pilots are logged; broad fields were too noisy to count as accepted final runs. The student supplied one Scopus export (68 rows) and three IEEE Xplore exports (9/25/3 rows); exact query-to-export mapping, deduplication and screening remain incomplete. Web of Science formal results have not been received. These partial runs do not close the reproducible three-database search or closest-work citation audit.
- Student evidence-reasoning exercise: `week_08_evidence_protocol_pack_eol/07_day1_evidence_reasoning_learning_guide.md` is an optional self-check, not a gate. Do not pause the research programme waiting for the student to classify sample sentences.
- Pack EoL content learning: `week_08_evidence_protocol_pack_eol/08_pack_eol_task_requirements_learning_guide.md` now provides the reference task cycle, the three core engineering distinctions, and a corrected R1–R6 explanation.
- Framework v1.0 input and decision rules: `09_framework_v1_input_requirements.md` separates task requirements from production conditions; `11_framework_v1_baseline_cards.md` and `13_framework_v1_decision_table_draft.md` contain configuration cards and four Gates. Status is **DRAFT — METHOD READY FOR PILOT, CASE RESULT NOT READY**. The 2026-09-28 public-source checkpoint corrects earlier overbroad UNKNOWN statements about dedicated and robotic contact mechanisms.
- R1–R6 correction checkpoint: treat R1 flexible-harness effects, R2 contact insertion, R3 electrical/safety state, R5 completion confirmation and R6 information closure as auditable functions rather than prescribed technologies. Treat R4 variation primarily as a production-condition axis. Do not carry forward the Week 06 claims that flexible harnesses necessarily require dual arms/full DLO estimation, that connector mating necessarily requires six-axis F/T control, or that HV safety is unique to battery manufacturing. The exact PLC/HVIL sequence and Robot–MES–Tester topology remain reference models, not observed target-site facts.
- Same-task equipment-baseline checkpoint: official Marposs and thyssenkrupp Pack EoL materials show that Pack transport/positioning and connector adaptation are separate configuration axes. Public alternatives combine trolley, conveyor or AGV loading with manual or automatic HV/communication connection. Framework v1.0 must therefore decompose `transport -> positioning -> connector adaptation -> test/safety cell -> information architecture`; do not equate AGV loading with mobile robotic connector manipulation or automatic contacting with a particular robot category. See `week_08_evidence_protocol_pack_eol/10_same_task_equipment_baseline_learning_note.md`.
- Candidate A public-source `F0`–`F3` pilot (2026-09-29): `week_08_evidence_protocol_pack_eol/15_candidate_a_public_evidence_checkpoint_2026-09-29.md` records ABB Baden **module** cell screening/orientation/insertion as the main industrial anchor, academic and supplier counterexamples, and SAIC E7 **Pack** loading as separate contextual evidence. Robotics relevance and case existence pass; placement acceptance, detailed responsibility, same-condition comparator evidence, and full case admission remain OPEN. This is not cross-case validation or an architecture result.
- Current active work: use public original sources to check the same-task Pack EoL manual/dedicated/robot configurations against mechanical insertion, connection acceptance, test permission, fault response, and safe disconnection; complete query logs and closest-work checking. Target-station Task/Condition/Safety Gates remain OPEN. For Candidate A, investigate observable placement acceptance and configuration-specific responsibility within the bounded `F0`–`F3` pilot; do not merge ABB module and SAIC Pack flows or begin full architecture ranking.

The immediate content-learning question inside the Week 08 cycle is:

> **How should the Pack EoL connector cycle be decomposed into observable task states and system functions, and which evidence-bounded requirements distinguish concrete robot/automation configurations without assuming capabilities from architecture labels?**

The next central learning/research question is:

> **How can the fixed RQs be converted into a reproducible evidence and case-assessment protocol, and which Week 06 Pack EoL claims survive source-level verification?**

Minimum target:

1. ~~finish the canonical baseline synchronization without changing the fixed title or RQs~~ — complete 2026-09-20;
2. ~~create Evidence Protocol v1 with search, screening, classification, and traceability rules~~ — established 2026-09-20;
3. run and log the formal database searches, then create and populate the Pack EoL Claim–Evidence Matrix;
4. audit the highest-impact Week 06 claims and record retain/downgrade/remove decisions;
5. specify the unresolved fields needed for Framework v1.0.

Optional extension only after the minimum target is credible:

- run a bounded `F0`–`F3` gate on Candidate A; do not begin its full architecture comparison yet.

At the start of each future session, inspect the latest current-week folder, this checkpoint, unresolved evidence rows, and any new Thomas feedback. Continue from the first unfinished step above rather than reopening the title or starting a new case.
