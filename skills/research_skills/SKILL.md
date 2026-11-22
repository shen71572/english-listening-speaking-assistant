# Research Skills

## Pick the right tool for the job

- Start from which step of the research pipeline the user is on, and pick the tool whose output matches it, topic and novelty, deep research, empirical analysis, figures, writing, review, or the full pipeline, before you write anything.

- Use Academic Research Skills for Claude Code (Imbad0202/academic-research-skills) for the full pipeline from research to publication: Deep Research, Academic Paper, Academic Paper Reviewer, and the Academic Pipeline orchestrator, with human-in-the-loop confirmation at every stage and integrity gates against hallucinated citations.

- Use Supervisor-Skills (HKUSTDial/Supervisor-Skills) for topic and novelty judgement: a HKUST professor's ten years of research experience distilled into callable AI skills, covering idea evaluation, introduction drafting, evidence-gated paper writing, polishing, deep research, and review across the paper lifecycle.

- Use PaperSpine (WUBING2023/PaperSpine) to turn a research question, data, or draft into an editable paper: it reviews literature, runs analyses, makes scientific figures, and delivers a paper with evidence you can check, using reference papers as writing models.

- Use Scientific-Agent-Skills (K-Dense-AI/scientific-agent-skills) for cross-disciplinary natural-science work: 177 ready-to-use validated skills plus 100+ scientific databases covering biology, chemistry, medicine, physics, engineering, and Earth science, on the open Agent Skills standard.

- Use Auto-Empirical Research-Skills (brycewang-stanford/Auto-Empirical-Research-Skills) for cross-disciplinary social-science work: 23,000+ agent skills for empirical research across 8 social science disciplines (economics, education, political science, psychology, sociology, communication, public administration, international relations), from data cleaning to top-journal submission, with rigor benchmarks.

- Use Academic Figure Generator (LigphiDonk/academic-figure-generator) for research figures: upload a paper, the AI analyses its content and generates prompts, then produces publication-quality figures in one click, with 50+ academic color schemes; it also ships an agent skill for use inside coding agents.

- Use Nature-Skills (Yuan1z0825/nature-skills) for top-journal writing and figures: 23 reusable research skills built around Nature-style academic expression, with Nature Polishing (paper polishing) and Nature Figure (research figures) as the core functions.

- Use Deep Research Skill for Claude Code (Weizhena/Deep-Research-skills) for verifiable deep research: a structured two-phase workflow, outline generation first and deep investigation second, with human-in-the-loop control at every stage and a final markdown report.

## Work through the research pipeline in order

- Topic and novelty: Supervisor-Skills for idea evaluation, plus PaperSpine and Academic Research Skills Deep Research for the literature check behind the novelty claim.
- Deep research: Deep Research Skill (outline, investigate, report) or Academic Research Skills Deep Research for survey-grade literature work.
- Cross-disciplinary analysis: Scientific-Agent-Skills for natural science, bioinformatics, chemistry, and medicine; Auto-Empirical Research-Skills for social-science empirical work (DID, RD, IV, matching, and related methods).
- Figures: Academic Figure Generator for paper-driven figure generation, Nature Figure for Nature-style figures.
- Writing and polishing: Academic Research Skills Academic Paper, PaperSpine for an editable draft, Nature Polishing for top-journal expression, Supervisor-Skills paper-writer and paper-polish.
- Review and revision: Academic Research Skills Academic Paper Reviewer and the Supervisor-Skills review skills, before any submission.
- Full-pipeline orchestration: Academic Research Skills Academic Pipeline, which runs research, writing, review, revision, and finalization as one supervised flow.
- Keep one tool per step and name the step each tool owns, so a failure points at one tool instead of the whole chain.

## Verify before you trust a tool

- Treat this list as the user collection, not as a verified review of each repo, and check a repo README and last update before you rely on it for a real deliverable.

- Search the repo for a maintained README and current examples when an install step or an API call fails, instead of guessing the fix.

- Say plainly when a tool does not fit the user request, and offer the closest tool from this list instead of forcing one in.

- Academic integrity is the hard boundary: AI is the copilot, not the pilot. The user remains the author and answers for every claim submitted. Verify every citation against its source before it goes into a paper; never present AI-generated text as the user's own unaudited work, and never help hide AI use.

## Naming notes

- The label ARIS properly belongs to a different repo: ARIS (Autonomous Research via Adversarial Multi-Agent Collaboration, Auto-Research-In-Sleep) is wanshuiyin/Auto-claude-code-research-in-sleep, 87 composable skills with cross-model review loops. The repo matching the name "Academic Research Skills for Claude Code" is Imbad0202/academic-research-skills; both are recorded here so the two are not confused.
- A second deep-research option with a similar name is 199-biotechnologies/claude-deep-research-skill, an enterprise-grade 8-phase pipeline with source credibility scoring.

## Available connectors

- [GitHub](/opt/hatch/connectors/github/CONNECTOR.md) for reading the repos in this toolkit.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- [Academic Research Skills for Claude Code](https://github.com/Imbad0202/academic-research-skills) — full-pipeline research agent (57,955 stars, updated 2026-11-21).
- [ARIS — Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) — autonomous ML research with cross-model review (19,553 stars, updated 2026-11-21).
- [Supervisor-Skills](https://github.com/HKUSTDial/Supervisor-Skills) — topic, novelty, and paper-lifecycle guidance (13,144 stars, updated 2026-11-21).
- [PaperSpine](https://github.com/WUBING2023/PaperSpine) — literature, analysis, figures, and editable papers from chat (6,372 stars, updated 2026-11-21).
- [Scientific-Agent-Skills](https://github.com/K-Dense-AI/scientific-agent-skills) — 177 natural-science skills and 100+ databases (58,001 stars, updated 2026-11-21).
- [Auto-Empirical Research-Skills](https://github.com/brycewang-stanford/Auto-Empirical-Research-Skills) — 23,000+ social-science empirical research skills (5,091 stars, updated 2026-11-21).
- [Academic Figure Generator](https://github.com/LigphiDonk/academic-figure-generator) — paper-to-figure generation platform and agent skill (3,003 stars, updated 2026-11-21).
- [Nature-Skills](https://github.com/Yuan1z0825/nature-skills) — Nature-style writing and figures (54,428 stars, updated 2026-11-21).
- [Deep Research Skill for Claude Code](https://github.com/Weizhena/Deep-Research-skills) — structured two-phase deep research (2,583 stars, updated 2026-11-21).

## Alternatives for better results

- Use the built-in research tools already available for a quick literature check or a short summary when installing a full skill library would be slower than the result is worth.

- Split a long paper workflow into stages and verify each stage (outline, draft, figures, citations) before moving to the next, so one bad stage never costs the whole paper.

- Ask the user for the field, the target venue, and the current stage (idea, draft, revision, submission) before you pick a tool, since those three answers decide which skill fits.
