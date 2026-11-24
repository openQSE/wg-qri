# openQSE QRI Workstream Meeting Summary

**Meeting:** openQSE QRI Workstream  
**Date:** November 24, 2026  

---

# Executive Summary

The meeting focused on two primary topics:

1. Reflections from SC26 and opportunities for continued community growth.
2. Development of an ISC paper intended to capture how the Quantum Resource Interface (QRI) specification is emerging through practical integration efforts.

Participants agreed that the openQSE presence at SC26 was highly successful, with strong attendance at quantum-focused sessions, BOFs, and demonstrations. There was broad support for organizing similar activities at ISC and SC Asia, and for expanding engagement with related efforts such as EQS3. 【1-d926cb】

The majority of the discussion centered on a proposed ISC paper led by Claudio Siqueira de Carvalho. The paper would describe a methodology of "learning a specification through integration," using experiences from integrating IBM, IQM, Pascal, QRMI, and QDMI implementations to derive requirements for a future QRI specification. The group discussed scope, categorization of functionality, mapping to existing interfaces, specification maturity assessment, and the boundaries of QRI responsibilities. 【1-d926cb】

---

# Attendees

- Yoonho Park
- Claudio Siqueira de Carvalho
- Amir Shehata
- Lukas Burgholzer
- Thomas Naughton
- Doug Oucharek
- Matthias Traube
- Eun Kyung Lee
- Marcel Walter
- Gabor Samu
- Abdur Rahman Hatim
- Cameron Brunner
- Marcel Walter

---

# Highlights

## SC26 Feedback

- SC26 quantum activities were viewed as highly successful, with many sessions attracting 100–200 attendees.
- The openQSE BOF generated substantial discussion and follow-on engagement from attendees.
- Naughton III, Thomas highlighted that including speakers from multiple layers of the software stack increased audience engagement and generated more focused questions.
- Multiple participants noted that attendees remained after sessions for extended side discussions and networking.

## Future Community Activities

### ISC

Participants expressed support for organizing an openQSE gathering or BOF at ISC. Lukas Burgholzer volunteered to help coordinate if needed.

### SC Asia

Shehata, Amir proposed creating an Asia-focused openQSE effort to improve engagement with organizations and researchers in the Asia-Pacific region that are difficult to involve because of time-zone differences.

### EQS3 Collaboration

Matthias Traube recommended closer engagement with the European Quantum Software and Systems Summit (EQS3) community due to significant overlap in interests and technical focus.

---

# ISC Paper Discussion

## Proposed Theme

The proposed paper theme is:

> Learning a specification through integration

The objective is not to publish a complete specification, but to document how specification requirements emerge through the practical integration of real quantum providers, interfaces, and software stacks.

## Paper Goals

The paper aims to:

- Document the progress made toward a QRI specification.
- Capture lessons learned from integrating multiple providers and interfaces.
- Provide a framework that allows contributions from participants responsible for different integrations.
- Identify specification requirements and future work.

## Proposed Methodology

Claudio Siqueira de Carvalho proposed an iterative methodology:

1. Integrate a new provider or interface.
2. Record findings and limitations.
3. Evaluate results against requirements.
4. Discuss findings within the community.
5. Refine the emerging specification.

Current integration efforts include:

- IBM
- IQM
- Pascal
- QRMI
- QDMI

These integrations provide the evidence used to derive specification requirements.

## Coverage and Maturity Tracking

Participants discussed tracking progress across multiple requirement categories ("axes"), including:

- Interface roles
- Submission
- Scheduling
- Device introspection
- Lifecycle management
- Telemetry
- Policies
- Resource management

The paper may include maturity indicators or coverage metrics to show where requirements are well understood and where additional work is needed.

---

# Major Technical Discussion

## Mapping QRI, QRMI, and QDMI

Several participants supported explicitly mapping QRI concepts to QRMI and QDMI concepts.

Benefits include:

- Showing where functionality originates.
- Identifying overlaps.
- Revealing capability gaps.
- Demonstrating how the common interface emerged from practical experience.

## Simplifying Requirement Categories

Shehata, Amir suggested reducing the number of requirement categories presented in the paper because the current breakdown may be overwhelming to readers unfamiliar with QFW internals.

The group generally agreed that a higher-level abstraction may improve readability.

## Hybrid Jobs vs Quantum Jobs

A significant discussion centered on whether QRI should support concepts related to hybrid jobs.

### Arguments for considering hybrid jobs

Shehata, Amir argued that:

- Quantum resource management may require understanding properties of larger hybrid workflows.
- Admission control and scheduling decisions may depend on hybrid-job characteristics.
- Resource managers such as Slurm may require richer information from QRI to make scheduling decisions.

### Arguments for limiting scope

Doug Oucharek cautioned that:

- QRI should remain focused on quantum resources.
- Job management responsibilities belong in higher layers.
- Expanding QRI too broadly risks turning it into "bloatware."
- Clear boundaries are needed between resource interfaces and workflow orchestration systems.

### Outcome

The group generally agreed that:

- The ISC paper should primarily focus on currently implemented functionality.
- Hybrid-job concepts may be discussed as future work or lessons learned rather than becoming a central focus of the paper.

## Provider Reservation Models

Marcel Walter described IQM's new **iteration mode**, which provides temporary exclusive access to a QPU for a sequence of operations.

Participants compared this capability to IBM sessions and discussed its potential relevance for future interface standardization efforts.

---

# Key Decisions

- Proceed with development of an ISC paper based on integration experience.
- Position the paper as a methodology and lessons-learned paper rather than a formal specification.
- Investigate mapping between QRI, QRMI, and QDMI concepts.
- Simplify requirement categories to improve readability.
- Keep the initial paper focused on validated integrations and existing functionality.

---

# Action Items

| Action Item | Owner(s) |
|-------------|----------|
| Continue developing the ISC paper and refine its structure. | Claudio Siqueira de Carvalho |
| Simplify and consolidate the current requirement-category framework. | Claudio Siqueira de Carvalho, Amir Shehata |
| Create mappings between QRI concepts and QRMI/QDMI capabilities. | Working Group |
| Determine whether IBM and Pascal integrations can be validated through both QRMI and QDMI paths. | Working Group |
| Develop a methodology for representing specification maturity and coverage. | Claudio Siqueira de Carvalho |
| Investigate ISC and SC Asia BOF/workshop opportunities. | Yoonho Park, Amir Shehata |
| Explore collaboration opportunities with EQS3. | European participants |
| Schedule weekly paper-development meetings through the ISC deadline period. | Yoonho Park |
| Add interested contributors to the paper meetings and Overleaf project. | Yoonho Park |

---

# Next Meeting

- Proposed: Next Wednesday at the same time.
- Purpose: Focused working session for ISC paper development.
- Interested participants should notify Yoonho Park so they can be added to the meeting invite and Overleaf collaboration space.
