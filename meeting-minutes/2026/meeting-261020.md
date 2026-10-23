# OQRI Workstream Meeting Summary 261020

## Executive Summary

The OpenQSE QRI Workstream focused on readiness for the upcoming SC demonstration, progress integrating IBM Quantum systems into QFW, and longer-term convergence between QRMI, QDMI, and the emerging QRI specification.

The overall assessment was positive:

- No major technical blockers were identified for the SC demonstration.
- Significant integration progress has been achieved across IBM, QFW, QDMI, QRMI, and compiler components.
- End-to-end execution through the full software stack has been successfully demonstrated.
- Several participants highlighted opportunities to improve usability, reduce workflow complexity, and address technical debt following SC.

The group agreed to prioritize successful SC delivery while postponing broader architectural cleanup and interface standardization efforts until Q1 next year.

---

## Attendees

- Yoonho Park
- Eun Kyung Lee
- Claudio Siqueira de Carvalho
- Brunner, Cameron
- Marcel Walter
- Lukas Burgholzer
- Matthias Traube
- Aleksander Wennersteen
- Shehata, Amir
- Abdur Rahman Hatim

---

## Highlights

### IBM Quantum Integration into QFW Progressing Well

Claudio Siqueira de Carvalho reported substantial progress integrating IBM Quantum support into QFW.

The team successfully validated three execution models:

1. Direct frontend-to-driver execution
2. Execution through a locally running QPMD
3. Full end-to-end execution through Slurm, site services, QPMD, and scheduler plugins

All three workflows are now functional. Remaining work is primarily focused on improving usability and reducing operational complexity for end users.

---

### SC Demonstration on Track

The compiler and integration teams reviewed end-to-end execution scenarios and identified no major blockers to the SC demonstration.

Current capabilities include:

- Qiskit-based application execution
- Compiler integration through QFW
- QRI-based hardware discovery
- Submission to backend quantum systems

While several engineering tasks remain, participants agreed that the current architecture is sufficient to support planned demonstrations.

Lukas Burgholzer noted that arbitrary user programs can already flow through the compiler stack to hardware targets without significant architectural obstacles.

---

### User Experience Concerns Emerging

A recurring theme throughout the discussion was the increasing complexity of the user experience.

Areas of concern included:

- Difficulty explaining QPMD-based workflows
- Exposure of internal implementation details to users
- JSON-centric interfaces versus higher-level SDK abstractions
- Native SDKs (especially Qiskit) often providing a simpler developer experience

The group generally agreed that future work should focus on making the platform easier to use and avoiding duplication of capabilities already available in vendor SDKs.

---

### QRI Specification Convergence Discussions

The workstream spent considerable time discussing how QRMI and QDMI could converge under a unified QRI framework.

Topics discussed included:

- Common device representations
- Resource discovery models
- Compiler-target interfaces
- Standard schema definitions
- Preservation of vendor-specific capabilities
- Interoperable topology and coupling-map formats

Consensus emerged around the need for common representations and metadata standards while preserving access to vendor-specific information required for advanced compiler optimizations.

---

### Expanded Cross-Platform Interoperability

Lukas Burgholzer reported that a QDMI device implementation for IBM cloud systems is now operational.

Benefits include:

- Additional interoperability validation
- Broader device coverage
- Expanded compiler testing scenarios
- Improved compatibility between independently developed ecosystem components

A pull request has already been submitted for integration into QFW.

---

### IBM Quantum Simulator Available for Development and Testing

The team discussed a simulator developed by Ohtani-san that:

- Uses Qiskit Aer internally
- Exposes the IBM Quantum System API
- Can be deployed through Docker Compose
- Supports local development environments
- Enables CI and integration testing without requiring cloud access

The simulator may become an important tool for future testing and onboarding activities.

---

## Risks and Open Issues

### Workflow Complexity

Although functional, the current end-to-end execution workflow remains difficult for users to understand and configure.

### Compiler Metadata Requirements

Some compiler workflows may require richer device metadata than currently exposed through normalized interfaces.

### Technical Debt

Several implementation shortcuts were intentionally accepted to meet SC timelines. These should be documented and addressed after the demonstration.

### Lack of Common Data Conventions

The following areas still require standardization:

- Coupling-map formats
- Shot-data representations
- Gate definitions
- Rotation conventions
- Cross-modality metadata

---

## Action Items

### High Priority

- Claudio Siqueira de Carvalho to submit a PR documenting and wrapping the three validated IBM/QFW execution paths.
- Claudio Siqueira de Carvalho to open an issue regarding long-running QPMD usability and workflow simplification.
- Compiler and HPE teams to continue SC demo integration work and target exposure improvements.
- QFW maintainers to review and merge the IBM QDMI device integration pull request.
- Organize a focused discussion on QRI schema design, compiler requirements, and standard device representations.

### Medium Priority

- Share IBM simulator repository information and deployment guidance with the broader community.
- Document accepted technical debt and establish a post-SC remediation plan.

### Strategic (Q1 Planning)

- Continue development of a unified QRI specification.
- Define standardized representations for quantum device capabilities and compiler-relevant metadata.
- Align QRMI and QDMI concepts under a common interoperability framework.

---

## Overall Assessment

**Status: Green**

The workstream demonstrated substantial progress across quantum runtime, device integration, compiler interoperability, and scheduling infrastructure. The SC demonstration appears achievable with the current architecture.

The primary challenges are no longer foundational integration issues but instead:

1. User experience simplification
2. Standardization of interfaces and metadata
3. Reduction of technical debt
4. Definition of a long-term QRI interoperability strategy

The team is well-positioned to deliver the SC demonstration while continuing architectural convergence efforts afterward.
