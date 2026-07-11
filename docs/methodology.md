# Methodology

The project used a qualitative, user-centred design methodology, combining research methods with iterative development practices to achieve five specific objectives.

## 1. Studying Fraud Experiences and Safety Gaps (Kampala)

- **Methods:** Interviews and document review.
- **Rationale:** Interviews gave direct, first-hand insight from mobile money users who had experienced or witnessed fraud — depth that surveys alone couldn't provide. Document review accessed verified reports and statistics from institutions like the Uganda Communications Commission (UCC) and Bank of Uganda, offering broader national context.
- **Instruments:** A semi-structured interview guide (see the Appendix in the full report) and a document review checklist for systematically extracting fraud patterns and awareness gaps from official reports and media publications.
- **Procedure:** Face-to-face interviews with students, market vendors, and boda-boda riders in Kampala and Wakiso.

## 2. Analysis of Findings and Requirements Determination

Interview and document review findings were translated into the functional and non-functional requirements that guided system design (see [`results.md`](results.md)).

## 3. Design

- **Tools:** Figma for high-fidelity UI mockups and user flows; draw.io for scenario logic diagrams.
- **Artifacts produced:**
  - UI mockups for splash, home, simulation, progress, and settings screens
  - Scenario flow diagrams mapping how users navigate scam simulations based on their choices
  - Voice script templates (Luganda and English), ensuring a realistic but safe tone
  - Low-fidelity wireframes to establish navigation before full visual design

## 4. Development

- **Approach:** Rapid Application Development (RAD) — iterative feedback and continuous user-centered refinement.
- **Stack:** Flutter SDK and Dart; `just_audio` and `audioplayers` for voice simulation; `sqflite` for offline local storage; GitHub for version control.
- **Modules implemented:**
  - **Scam Simulation Module** — interactive scenarios with synchronized voice guidance
  - **Decision Tracking Module** — records user choices and provides immediate feedback
  - **Video Viewing Module** — educational animations on fraud tactics
  - **Progress Monitoring Module** — tracks learning milestones via local SQL storage
  - **Settings Module** — language and audio adjustments
  - **Backup Module** — local data export and future cloud synchronization

## 5. Testing and Validation

- **Formative testing:** Conducted during development with a small group of students and market vendors to refine scenario/voice clarity.
- **Summative testing:** Structured post-development sessions where participants completed specific tasks and gave feedback.
- **Instruments:** A test data matrix covering seven key cases (scenario playback, decision recording, offline access, etc.) and a simplified System Usability Scale (SUS) administered to 15 users.

Full results are documented in [`results.md`](results.md).
