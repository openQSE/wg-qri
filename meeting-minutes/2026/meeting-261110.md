# openQSE QRI Workstream Meeting Summary

## Summary

This workstream meeting focused on two primary topics:

1. Refinement of the upcoming openQSE Birds-of-a-Feather (BOF) session agenda and presentation structure.
2. Discussion and convergence on an openQSE/QRI reference architecture diagram to support SC demonstrations and community messaging.

The group aligned on making the BOF more workflow-centric, increasing discussion time, incorporating workflow technologies more explicitly, and simplifying the architecture diagrams while preserving key technical concepts. Significant discussion focused on how to present workflows, orchestration, QRI technologies, and system layers in a way that is both technically accurate and accessible to a broader audience.

---

# Attendees

- Yoonho Park
- Amir Shehata
- Thomas Naughton III
- Doug
- Shweta Salaria
- Matthias Traube
- Michael Sandoval
- Michael Ferguson
- Claudio Siqueira de Carvalho
- Francesco Medina
- Yogesh Simmhan
- Philipp Seitz
- Jorge Echavarria
- Eun Kyung Lee
- Marco De Pascale
- Ben Lau

---

# Key Highlights

## 1. BOF Agenda Updated to Emphasize Workflows

The group agreed to reduce the QRI presentation allocation from 12 minutes to 6 minutes and reallocate time toward workflow-related content. Workflows were recognized as a major architectural component that deserves more visibility during the BOF.

## 2. Runtime Working Group Section Likely Reduced

Amir Shehata volunteered to give up the Runtime Working Group slot to create additional time for workflow and architecture discussions.

## 3. Focus on Roadmap Rather Than Repeating Demonstrations

Since the BOF follows the DOE booth demonstration, participants recommended focusing on:

- Lessons learned
- Integration challenges
- Future directions
- Interface standardization
- Community roadmap

rather than repeating the demo itself.

## 4. Increased Audience Interaction

Participants agreed that the BOF should include more discussion and audience engagement by:

- Reducing presentation time slightly
- Increasing Q&A time
- Using stronger moderation
- Capturing questions during presentations rather than interrupting speakers

## 5. Slido Considered for Question Management

Michael Sandoval proposed using Slido to collect and prioritize audience questions during the BOF session.

## 6. Architecture Diagram Simplification

The team reviewed architecture diagrams developed by Yoonho Park and Amir Shehata. Consensus areas included:

- Simplifying QFW-related components
- Better representing application processes
- Improving alignment with openQSE working groups
- Reducing unnecessary complexity
- Clarifying representation of QRMI and QDMI

## 7. Layering and Orchestration Discussions

Participants discussed separating:

### Application Orchestration

- Prefect
- Tierkreis
- StreamFlow

### System Orchestration

- Slurm
- Flux

This structure received support and may help improve architectural clarity.

## 8. Need for Multiple Diagrams

Participants noted that a single diagram is currently being used to represent both:

1. Reference architecture
2. Runtime execution and plumbing

The emerging consensus favored:

- One simplified architecture diagram
- Separate execution-flow diagrams for demonstrations

## 9. Federation Demonstration Progress

Jorge Echavarria presented plans for a federated demonstration involving MQV/MQSS, AWS, LRZ, and PlanQK-style environments. The discussion emphasized federation, interoperability, and user experience rather than promoting specific technologies.

---

# Decisions

| Decision | Outcome |
|-----------|---------|
| Reduce QRI presentation time | Approved |
| Add workflow-focused BOF content | Approved |
| Reallocate Runtime WG slot | Supported |
| Increase discussion and Q&A time | Supported |
| Evaluate Slido for audience questions | Supported |
| Continue architecture simplification efforts | Agreed |
| Emphasize roadmap and integration over demo repetition | Agreed |
| Proceed with federation demonstration concept | Supported |

---

# Action Items

| Owner | Action |
|---------|---------|
| Amir Shehata | Coordinate with Sebastian on workflow presentation ownership and content. |
| Thomas Naughton III | Update BOF agenda and speaker assignments. |
| Thomas Naughton III | Maintain a consolidated slide deck for the BOF. |
| Yoonho Park | Confirm revised QRI presentation allocation with Lucas. |
| Yoonho Park and Thomas Naughton III | Moderate BOF timing and audience questions. |
| Yoonho Park and Amir Shehata | Finalize the architecture diagram. |
| Amir Shehata | Consolidate architecture feedback from the meeting. |
| Yogesh Simmhan | Incorporate workflow-planning concepts into demonstration diagrams. |
| Francesco Medina | Align StreamFlow demo materials with the agreed architecture model. |
| Michael Sandoval / Team | Evaluate Slido for audience engagement. |
| Yoonho Park | Send finalized BOF agenda slide to Thomas Naughton III. |

---

# Overall Readout

The meeting was productive and resulted in substantial alignment on both BOF structure and technical messaging. The principal remaining task is converging on a streamlined architecture diagram that clearly communicates the relationship among applications, workflows, orchestration platforms, QRMI/QDMI interfaces, and quantum resources. The team appears aligned around emphasizing workflows, integration, federation, and future roadmap planning as key openQSE messages for SC.
