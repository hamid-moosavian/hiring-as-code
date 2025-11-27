# Hiring as Code

An open framework for running engineering hiring like a versioned, tested, observable system.  
Created by HiringStack.

---

## What is Hiring as Code?

Hiring as Code is a practical way for engineering teams to run hiring with the same discipline they use for software:

- Version controlled job descriptions  
- Defined and repeatable interview pipelines  
- Structured evaluation that acts like a test suite  
- Measurable, observable hiring outcomes  
- Continuous improvement instead of ad hoc changes  

This repo is the canonical home of the framework.

**Current version:** `v0.1`

**Visual diagrams:** See the [diagrams folder](./diagrams/) for visual representations of each pillar ([view diagrams](./diagrams/DIAGRAMS.md)).

---

## Core Principles

Hiring as Code starts from a simple idea:

> Hiring is a system. Systems become reliable when they are versioned, tested, automated, observable, and continuously improved.

The framework focuses on seven pillars.

---

## Pillars of Hiring as Code (v0.1)

### 1. Version Controlled Job Descriptions (JD as Code)

Treat every job description like a code artifact.

- Use semantic versions (for example: `v1.0`, `v1.1`, `v2.0`)
- Track what changed and why
- Branch JDs for different teams or seniority levels
- Review JDs like code reviews, with comments and approvals

**Outcome:** Clear, aligned, and auditable role definitions instead of random Google Docs.

**Example:**
```
senior-backend-engineer-v2.1.md
- v2.1: Added Kubernetes requirement (team migrating Q2 2025)
- v2.0: Increased experience requirement from 3+ to 5+ years
- v1.0: Initial version
```

---

### 2. Pipeline as Code (Structured Hiring Workflow)

Define the hiring process declaratively.

- Represent interview stages in a pipeline file (YAML or similar)
- Specify stages, ownership, success criteria, and guardrails
- Use conditional logic for seniority, role type, or location
- Propose changes through pull requests rather than ad hoc tweaks

**Outcome:** Consistent, fair, and repeatable process instead of every hire being a one off.

**Example:**
```yaml
pipeline:
  stages:
    - name: phone_screen
      owner: recruiter
      duration: 30min
      success_criteria: culture_fit, basic_qualifications
    
    - name: technical_assessment
      owner: senior_engineer
      duration: 90min
      success_criteria: coding_ability, problem_solving
```

---

### 3. Test Suite Design (Structured Evaluation)

Treat your interview loop as a test suite for the role.

- Define the competencies you must assess for each role
- Map questions and exercises to those competencies
- Use rubrics with clear pass or fail thresholds
- Ensure coverage so each competency is evaluated in a specific stage

**Outcome:** Better signal, less noise, and fewer "gut feel" decisions.

**Example:**
```
Required Competencies:
✓ System Design        → Tested in: System Design Interview
✓ Code Quality         → Tested in: Technical Assessment
✓ Communication        → Tested in: Team Fit Conversation
✓ Problem Solving      → Tested in: Technical Assessment
✓ Cultural Alignment   → Tested in: Values Interview
```

---

### 4. Continuous Integration for Feedback

Handle interview feedback like CI checks.

- Set SLAs for submitting feedback after interviews
- Use tools or simple automation to nudge when feedback is missing
- Trigger debriefs automatically when all feedback is in
- Require all checks to pass before moving to offer

**Outcome:** Faster decisions and fewer stalls caused by missing or late feedback.

**Example:**
```
Candidate: Jane Smith
Status: Waiting on feedback (2/4 complete)

✓ Phone Screen       - Submitted (pass)
✓ Technical Screen   - Submitted (pass)
⏳ System Design     - Pending (due in 18 hours)
⏳ Team Fit          - Pending (due in 18 hours)

Action: Auto-reminder sent to interviewers
Next: Debrief auto-scheduled for Thursday 2pm
```

---

### 5. Deployment and Rollback (Onboarding as Release)

A hiring decision is a deployment into production.

- Create 30, 60, and 90 day plans before the start date
- Define what "good" looks like at each checkpoint
- Run lightweight "health checks" at those milestones
- Have clear protocols for handling misalignment or performance issues

**Outcome:** Better ramp up, fewer surprises, and more honest early conversations.

**Example:**
```
30 Days:
- Complete onboarding checklist
- Ship first small feature
- Health Check: Can navigate codebase independently?

60 Days:
- Own one project end-to-end
- Participate in on-call rotation
- Health Check: Delivering at expected pace?

90 Days:
- Mentoring junior engineer
- Leading technical decisions
- Health Check: Meeting senior engineer bar?
```

---

### 6. Monitoring and Observability (Hiring Metrics)

You cannot improve what you do not measure.

Track at least:

- Conversion rates between pipeline stages  
- Time in stage and time to hire  
- Source effectiveness and quality of hire by source  
- Offer acceptance rate  
- Early performance signals and retention for new hires  

**Outcome:** Hiring becomes a measurable system instead of a black box.

**Example Dashboard:**
```
Pipeline Health (Last 30 Days)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Phone Screen → Technical:     68% conversion
Technical → Onsite:           45% conversion
Onsite → Offer:              60% conversion
Offer → Accept:              85% acceptance

Time-to-Fill: 42 days (target: 35 days)
Top Source: Employee referrals (40% of hires)
Quality Score: 4.2/5.0 (90-day manager rating)
```

---

### 7. Security and Compliance (Bias and Risk Controls)

Shift hiring risk and bias checks to the left.

- Run JDs through a "bias linter" before publishing
- Calibrate interviewers on rubrics and examples
- Standardize decision making and documentation
- Keep an audit trail of evaluations, not just the final yes or no

**Outcome:** Safer, more inclusive hiring with fewer surprises later.

**Example:**
```
JD Bias Scan Results:
⚠️  Warning: "Rock star" (gendered language)
⚠️  Warning: "Recent graduate" (age bias)
✓  Pass: Years of experience reasonable (3-5 years)
✓  Pass: No unnecessary degree requirements
✓  Pass: Inclusive language check passed
```

---

## Where the Analogy Breaks

Hiring as Code is a useful mental model, but hiring is still about people, not machines. The analogy has limits.

- **Chemistry cannot be unit tested.** Genuine rapport and team fit do not map neatly to test cases.  
- **Growth is unpredictable.** People evolve in ways that cannot be fully inferred from past performance.  
- **Same process does not guarantee the same outcome.** Two candidates through the same pipeline can have very different long term results.  
- **You cannot rollback cultural impact.** A mis hire can leave lasting effects on culture and trust that are not reversible.  
- **Human context matters.** Life circumstances, motivations, and emotional load never fit cleanly into an engineering concept.

The framework provides structure. Your judgment provides wisdom.

---

## What This Framework Is NOT

This is not:
- HR theory
- An analogy for fun
- A metaphor stretched too far
- A replacement for human judgment

This is a **practical operating model** for engineering-led hiring.

The analogy works because it maps directly to real hiring problems that engineering leaders face.

---

## Repository Model (Conceptual View)

One way to think about Hiring as Code is as a repository that holds the system for how you hire:

```text
/hiring-system/
  /specs/              # Job descriptions and role definitions
    senior-backend-v2.1.md
    frontend-lead-v1.3.md

  /pipeline/           # Defined interview flows and criteria
    interview-process.yaml
    evaluation-rubric.md

  /tests/              # Question banks and exercises
    technical-questions.md
    system-design-prompts.md

  /deploy/             # Onboarding and ramp up plans
    onboarding-checklist.md
    90-day-plan.md

  /monitoring/         # Metrics and reporting
    metrics-dashboard.yaml

  README.md            # How your hiring system works
  CONTRIBUTING.md      # How to propose changes
```

You do not need this exact structure in your company. The point is to treat your hiring system as something you can version, review, and improve, not as a set of ad hoc habits.

---

## How to Use This Framework

You can start very small:

1. **Pick one pillar that hurts the most** in your current process.
2. **Write down how you actually do it today.**
3. **Compare that to the description** in this framework.
4. **Define one change** you can roll out in the next hiring cycle.
5. **Treat that change like a code change:** document it, communicate it, and review the outcome.

**Recommended starting points:**

- **Easiest to start:** Pillar 1 (Version Control) - Just version your next JD and document why
- **Highest impact:** Pillar 3 (Test Suite Design) - Map competencies to interviews and find gaps
- **Most transformative:** Pillar 6 (Monitoring) - Start tracking 3 metrics and review monthly

You can also:
- Fork this repo and adapt the framework to your org
- Add your own examples under `/examples`
- Link it in your internal hiring docs as the "engineering view" of your process

---

## Versioning

This repo uses simple versioning for the framework itself:

**v0.1** (November 2025)
- Initial public framework
- Seven pillars defined
- "Where the Analogy Breaks" section included
- Concrete examples for each pillar
- Visual diagrams for each pillar

Future versions can add:
- Concrete templates and sample configs
- Metrics dashboards and reports
- Case studies from teams using this model

---

## Roadmap (High Level)

Planned next steps for this repo:
- Add concrete templates and examples for each pillar
- Add stories and case studies from real teams using this model
- Community contributions and variations

---

## Contributing

This is v0.1 - a starting point, not a finished product.

Have you implemented one of these pillars? Found a gap? Have a better approach?

**Ways to contribute:**
- Open an issue with your experience or questions
- Submit a pull request with improvements
- Share your own examples or templates
- Suggest new pillars or refinements

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

---

## About

Hiring as Code is part of the [HiringStack](https://hiringstack.io) project.

Created by [Hamid Moosavian](https://github.com/hamid-moosavian) based on 20+ years of engineering leadership and hiring experience.

The goal is to give engineering leaders practical tools and mental models for building better hiring systems.

**Feedback welcome:** Open an issue or reach out via [LinkedIn](https://linkedin.com/in/hamid-moosavian).

---

## License

MIT License - see [LICENSE](LICENSE) file for details.
