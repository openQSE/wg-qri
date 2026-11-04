# openQSE QRI Workstream Meeting Minutes

# Attendees

- Claudio Siqueira de Carvalho
- Lukas Burgholzer
- Aleksander Wennersteen
- Amir Shehata
- Abdur Rahman Hatim

---

# Executive Summary

The meeting focused on preparations for the SC26 demonstration and progress across the Quantum Resource Interface (QRI) ecosystem. Significant updates included IBM and Pasqal QDMI integrations, continued work on cloud and on-prem resource support, and efforts to integrate QDMI and QRMI within QFw.

A major discussion centered on a proposed runtime architecture intended to simplify application portability by abstracting backend selection, compiler choice, and device targeting. The group also reviewed telemetry deployment, Slurm integration, resource acquisition workflows, credential management, and support for SQD workflows.

Overall, the workstream is progressing toward a more portable, device-agnostic architecture while addressing practical deployment and demonstration requirements for SC26.

---

# Highlights

## SC26 Demo Planning

- IBM QDMI device integration is operational for cloud-connected deployments.
- Native support for on-prem IBM deployments is under active development.
- Pasqal QDMI integration has been implemented and is approaching release readiness.
- The team is evaluating whether Pasqal workloads can be incorporated into the SC26 demonstration.
- Concerns were raised about relying on live demonstrations due to queue times and operational uncertainty.
- Pre-recorded demonstrations were viewed as a lower-risk option.

## SC26 Presentation Strategy

A potential outreach approach was discussed:

- Deliver short booth presentations (~5 minutes).
- Supplement presentations with longer recorded technical demonstrations.
- Provide attendees with access to more detailed technical content online.

## Runtime Architecture

A new runtime architecture concept was presented with the goals of:

- Decoupling applications from specific backends.
- Automatically selecting compilers and target devices.
- Choosing appropriate compilation pathways and formats.
- Routing jobs to resources via QRI.

The proposed model would create execution "routes" containing:

- Application framework
- Compiler selection
- Input/output formats
- Target device

The concept received positive feedback and appears aligned with ongoing compiler and runtime efforts.

## Compiler and Runtime Integration

Discussion focused on:

- Compiler awareness of device capabilities.
- Automatic selection of supported output formats.
- Capability-driven compilation.
- Support for multiple software ecosystems including OpenQASM, Qiskit, PennyLane, and native compiler workflows.

The team noted that compiler capability discovery remains an open design challenge.

## Resource Acquisition and Credential Management

The group discussed future Acquire API workflows.

Proposed direction:

- Credentials remain managed within QPM services.
- Users receive reservation identifiers rather than device credentials.
- Reservation identifiers propagate through scheduler environments.
- Provider credentials remain hidden from end users.

This approach improves security and simplifies the user experience.

## Telemetry and RPC Progress

Updates included:

- Telemetry infrastructure is complete and ready for testbed deployment.
- A C-based RPC implementation exists and requires further validation.
- RPC capabilities are unlikely to be demonstrated at SC26.

## IBM Integration Progress

Current work includes:

- End-to-end circuit execution through QFw.
- IBM simulator integration.
- Ongoing pull request reviews.
- Evaluation of QMI updates to improve diagnostics and exception handling.

---

# Action Items

| Owner | Action | Priority |
|---------|---------|----------|
| Amir | Share SC26 demo/video proposal and collect feedback. | High |
| All Participants | Evaluate creation of recorded technical demonstrations for SC26. | High |
| Aleksander | Follow up with Doug regarding Pasqal testing and integration readiness. | High |
| Lukas | Share relevant compiler/runtime integration references and documentation. | Medium |
| Amir | Publish runtime architecture proposal for broader review. | High |
| Compiler Working Group | Review runtime abstraction and compiler-selection concepts. | Medium |
| Claudio | Address reviewer feedback on IBM QFw and Slurm integration pull requests. | High |
| Claudio | Open issues related to QMI services, configuration, and status handling. | Medium |
| ORNL Team | Deploy and validate telemetry services on the Janus testbed. | Medium |
| Team | Continue interoperability testing across IBM and Pasqal QDMI/QRMI integrations. | High |
| Team | Evaluate QMI upgrades to improve diagnostics and exception propagation. | Medium |
| Amir | Continue development of reservation and Acquire API workflows. | High |
| Claudio | Share SQD-related Slurm and telemetry updates with Yu. | Medium |
| SQD Team | Investigate and resolve Slurm communication issues. | High |

---

# Risks and Open Questions

| Area | Question |
|--------|----------|
| SC26 Demonstrations | Should the team prioritize recorded demonstrations over live execution? |
| Runtime Design | How much abstraction should be provided versus exposing advanced compiler controls? |
| Compiler Discovery | How should compiler capabilities be represented and queried? |
| Resource Acquisition | How should Acquire APIs integrate with schedulers and QPM services? |
| QMI Services | Should resource health checks gate access to other APIs? |
| Production Runtime | What is the path from Python prototypes to production-grade runtimes? |

---

# Bottom Line

The QRI workstream continues to make strong progress toward the SC26 demonstration, with IBM and Pasqal integrations advancing rapidly and runtime architecture discussions converging around a more portable, backend-agnostic model. Near-term priorities are completing integration work, validating telemetry and resource-acquisition workflows, refining the runtime architecture proposal, and finalizing demonstration content for SC26.
