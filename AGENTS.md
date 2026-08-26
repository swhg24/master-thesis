# Master Thesis Project Instructions

This repository supports Fuhan Liao's thesis at PEM, RWTH Aachen.

Thomas's supervisor-provided working title and the non-negotiable direction anchor are:

> **Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies**

This is the working title supplied by Thomas, not yet a final registered title. Every weekly case, evidence review, and candidate problem must remain traceably connected to **robotic systems in lithium-ion battery manufacturing**. The PDF title uses `Battery Manufacturing`, while the task paragraph says `along the battery cell production value chain`; therefore cell versus module/pack scope must be made explicit and confirmed with Thomas, not decided by an internal exclusion rule. A battery-equipment or material-flow description without a robotics question is not sufficient merely because it occurs inside a battery factory.

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
- The provisional thesis route is **one deep reference case plus two to three adjacent battery-manufacturing cases**. Use the deep case to develop a reusable `Task -> Requirement -> Capability -> Suitability` assessment framework, then test and refine it through cross-case comparison.

## Always apply

- Treat `docs/pem_thesis_requirements.md` as the project reference for PEM process, writing, citation, figure, submission, and colloquium requirements. Read the relevant section before advising on thesis structure, registration, writing, citations, figures, submission, or presentation.
- Treat `docs/collaboration_and_pacing.md` as the project reference for the six-month working rhythm, weekly planning format, GPT/Codex/student responsibilities, meeting-feedback loop, and Git handoff. Read it before proposing or executing a new weekly plan.
- Treat `docs/research_direction_guardrails.md` as the mandatory project reference for the thesis direction, current use case, robotics-relevance gate, scope boundaries, and candidate-decision rules. Read it before proposing a weekly plan, selecting or narrowing a case, changing a research question, or deciding that a technical detail belongs in the thesis.
- Distinguish clearly between: (1) official PEM/RWTH requirements, (2) supervisor guidance, (3) literature-supported findings, and (4) current working hypotheses. Never present a hypothesis as an official rule or established result.
- Preserve an evidence chain for research claims: claim -> source -> exact page/section when available -> implication for battery manufacturing -> implication for robotics.
- Do not invent cycle times, accuracy, yield improvements, costs, ROI, or maturity levels. Label missing evidence explicitly.
- Prefer peer-reviewed and recent international literature for the scientific argument. Industry and supplier sources may support implementation examples but must not substitute for academic evidence.
- Keep the thesis scope centered on lithium-ion battery manufacturing and always state whether evidence concerns cell, module, or pack production. Module/pack production is a legitimate candidate scope to put to Thomas because the working title is broader and the strongest direct humanoid cases currently occur there; it is neither silently included nor pre-emptively excluded before his decision. Recycling remains adjacent unless Thomas broadens the boundary. Detailed robot-control algorithms remain outside the core unless the research question later requires them.
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

## Registration proposal checkpoint (2026-08-20)

Treat `docs/thesis_registration_consensus_2026-08-20.md` as the canonical decision record for the current proposed title, research questions, research problem, scope, method, expected contributions, thesis story, risks, and post-registration route. This is a **student–GPT–Codex consensus pending Thomas's confirmation**, not an approved or registered supervisor decision. If Thomas changes any part, update that record, this checkpoint, the direction guardrails, and the current case plan together.

The proposed registration title is:

> **Task-Based Assessment of Robotic Systems in Battery Manufacturing: Application Potential and Implementation Strategies**

Proposed German title:

> **Aufgabenbasierte Bewertung von Robotersystemen in der Batteriefertigung: Anwendungspotenziale und Implementierungsstrategien**

The proposed research questions are:

1. **Which task characteristics and process and production requirements determine the application potential of robotic systems in selected battery-manufacturing use cases?**
2. **How do different robotic-system architectures compare with dedicated, fixed-purpose automation in their conditional suitability under varying task and production conditions?**
3. **How can the selected robotic applications be implemented in industry while addressing technical, economic, and integration-related barriers?**

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

The thesis remains an **evidence-based comparative multiple-case assessment**, with Pack EoL test-connector handling as the first deep reference case and one to two evidence-sufficient adjacent applications used to test transfer and support cross-case conclusions. Week 06 provides a method prototype, not the final thesis contribution. Humanoid/mobile dual-arm systems are candidates to compare, not a preferred answer; dedicated fixed-purpose automation, fixed industrial robots, cobots/mobile systems, and relevant manual baselines remain legitimate comparators.

The unresolved registration-scope question is whether Thomas intends selected module/pack applications to be explicitly included alongside battery-cell-production applications. Do not silently resolve the difference between the PDF phrase `battery cell production value chain`, the broader working title `Battery Manufacturing`, and Thomas's acceptance of Pack EoL. State the production level of every case and obtain Thomas's confirmation in the registration exchange.

Do not mutate the title or RQs merely to fit new evidence, a new Skill template, or weekly-plan continuity. A change requires an explicit decision record triggered by Thomas's feedback, a defeated relevance/evidence gate, or a materially better and feasible thesis framing.

## Current research direction

- Week 01 established: battery fundamentals -> process requirements -> initial robotics opportunities.
- Week 02 established an evidence-based process/problem/robotics map, but supervisor feedback found the work too high-level and requested one step-by-step learning case.
- Week 03 completed the formation-aging-testing tray-transport learning cycle: process functions, conditional carrier flows, request/handover events, blocking/starvation, AGV control layers, and the evidence boundary of one rechargeable-battery AGV case. It produced a conditional conceptual model, not a confirmed factory layout.
- Week 04 completed a nearest-neighbor literature and counterexample audit. It showed that cell-finishing configuration research already includes some carrier functions, physical interfaces, and intralogistics transitions. Candidate A (operation-level carrier handover) and Candidate B (exception-triggered carrier flow) remain hypotheses, not established gaps.
- Week 05 uses one disclosed formation-loading architecture to fill an interface unknown from Week 03–04. Architecture B (`inbound machine 27 -> stacker crane 28 -> formation device 3`) is a **non-AGV fixed-automation reference/baseline**, not the thesis topic and not direct evidence for a robotic transport case.
- The Day 3 robotics-relevance audit found no direct evidence that a formation-specific condition changes the B2 stacker-crane task, and the fixed-automation interface does not by itself establish the robotics relevance intended by Thomas. B2 therefore remains a learning baseline/counterexample and exits the active thesis-candidate path; do not deepen it through further PLC, contact, positioning, or handover-state detail unless a new concrete robotic target case is supplied.
- Direction reset on 2026-08-12: return to Thomas's original industry-forward task profile and explore strongly robotics-related battery-manufacturing use cases. Give explicit attention to humanoid robots as requested in the student's report of the latest supervisor guidance, while comparing them against industrial robots, cobots, mobile robots, and dedicated automation rather than assuming that a humanoid form is advantageous.
- Current evidence indicates direct industrial humanoid deployments in battery module/pack manufacturing, including cell handling/loading and high-voltage testing, but no confirmed direct deployment in core battery-cell-manufacturing steps has yet been established. This evidence supports asking Thomas to choose the production-level boundary; it does not itself decide the boundary.
- The A/B/C case-selection checkpoint has progressed: in the 2026-08-12 meeting Thomas accepted Pack EoL testing as a workable direction, and the student selected Candidate B for further study with Thomas's agreement. This is a provisional deep reference case, not a final registered title or the thesis's only case.
- Week 06 uses **battery-pack EoL test-connector handling** as the first deep reference case. DCR remains adjacent until evidence confirms that the same handling abstraction, connector, station, or robot applies. CATL/Spirit AI `Xiaomo` is an industrial anchor, not the object of the thesis and not independent proof of performance.
- Week 06 develops the first `Task -> Requirement -> Capability -> Suitability` framework by comparing dedicated automation, fixed industrial robots, and humanoid/mobile dual-arm systems. It must derive requirements from the manufacturing task before examining humanoid attributes and must produce conditional suitability rather than a brand ranking.
- Candidate A (cell identification, grasping, and loading) is the leading adjacent case to test framework transfer after Week 06; Candidate C (multi-station material handling and picking) remains a later option pending a concrete flow object and task boundary. Do not open all cases in parallel.
- The case charter records a stable analytical boundary and evidence minimum without turning the deep case into an immutable single-case thesis. Change the route only through an explicit decision record when supervisor direction changes, direct evidence defeats relevance, or a credible evidence strategy cannot support the intended claims.
- AGV fleet size/dispatching and robustness remain possible later directions, not current conclusions. Advance only if they answer a defined research question and process understanding, evidence, transparent inputs, and the evaluation strategy make them useful.
