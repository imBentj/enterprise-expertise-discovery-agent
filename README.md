# Enterprise Expertise Discovery Agent

A working AI proof of concept exploring evidence-backed expertise discovery for project and solution leads preparing for client opportunities.

> **Status:** Published proof of concept; synthetic data only. Not production-ready. No live internal-system integration. Business impact and production readiness have not been validated.

## Problem
Project leads may need to identify people who collectively cover a client's required capabilities. Searching keywords alone can miss relevant context and makes it difficult to distinguish documented experience from assumptions.

## Proposed experience
1. Describe the client requirement in natural language.
2. Identify relevant employee profiles and documented evidence.
3. Separate documented facts from inferred suitability and gaps.
4. Suggest a complementary team when no single profile covers all requirements.
5. Ask a clarifying question when the request is too ambiguous.

## Product principles
- Treat the supplied profiles as the source of evidence.
- “Not documented” means unverified in the profile; it does not prove a person lacks the capability.
- Do not claim an individual has multiple capabilities unless the profile supports each claim.
- Do not silently relax strict requirements to force a match.
- Keep staffing decisions with a human reviewer.
- Use synthetic profiles in this demonstration; do not add confidential or personal employee data.

## Repository contents
- `data/enterprise_expertise_sample_profiles.csv` — 12 fictional employee profiles.
- `data/enterprise_expertise_test_queries.csv` — evaluation queries.
- `prototype/enterprise_expertise_discovery_prototype_v3.html` — earlier standalone prototype/evaluation UI; it is not the same as the deployed React application.
- `docs/product_requirements_and_evaluation.docx` — product requirements and evaluation notes.
- `presentation/interview_deck.pptx` — interview presentation.
- `src/` and the root application manifests should contain the exported Google AI Studio application source once added (see below).

## Add the deployed app source
The deployed app was generated/refined in Google AI Studio Build mode and uses a React frontend with a Node.js/Express/TypeScript backend that calls Gemini. Export or download the current source from AI Studio and add the relevant source files to this repository. Expected files may include `src/`, `server.ts`, `package.json`, a lockfile, Vite configuration, and any public assets. Preserve the actual structure from the export rather than creating empty placeholder files.

**Do not commit secrets.** Keep your Gemini API key in an environment variable such as `GEMINI_API_KEY`. Add a `.env` file locally only; `.env` is ignored by Git. Never paste an API key into frontend code, README files, screenshots, or commits.

## Run locally (after adding the application source)
1. Install a supported Node.js LTS version.
2. Install dependencies using the package manager/lockfile from the exported app, for example `npm install`.
3. Create a local `.env` file containing `GEMINI_API_KEY=your_key_here` (do not commit it).
4. Run the scripts documented in the exported `package.json`, usually a development command such as `npm run dev`.

The exact commands should be confirmed against the exported source and its `package.json` before publishing them as final setup instructions.

## Evaluation scenarios
1. Oracle Fusion Procurement knowledge + AI workflow automation.
2. Strict production AI agent requirement with Oracle Fusion integration, security controls, exception handling, and measurable business benefits.
3. Oracle reporting + procurement + AI automation; do not attribute both to an individual unless their profile supports both.
4. Retail operations + AI workflow automation + human review.
5. Ambiguous request: “Find someone who can improve operations.” The application should clarify before recommending candidates.

The five scenarios were manually tested on the published proof of concept. These checks are qualitative examples, not a statistically validated accuracy benchmark. The deterministic fallback path was reviewed in code, but dedicated end-to-end failure-injection testing has not been completed.

## Limitations and next steps
- Validate the problem and baseline workflow with project leads.
- Build a larger reviewed evaluation set and assess capability coverage, ranking quality, and unsupported claims.
- Test ambiguity, edge cases, and model/API failure paths.
- Review privacy, access controls, auditability, and profile freshness before any pilot using approved real data.
- Measure time to a validated shortlist, recommendation precision, coverage, trust, and adoption.

## Live proof of concept
https://enterprise-expertise-discovery-agent-677011801904.asia-southeast1.run.app

The live deployment is a demonstration only and may change independently of this repository.
