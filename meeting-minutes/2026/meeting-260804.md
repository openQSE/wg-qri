# QRI Workstream Meeting Summary 260804

## Attendees

- Yoonho Park
- Greg Arteen
- Patrick Hopf
- Munetaka Ohtani
- Oscar Wallis
- Cameron Brunner
- Matthias Traube
- Claudio Siqueira de Carvalho
- Tim Osborne
- Woong Shin
- Michael Sandoval
- Eun Kyung Lee
- Aleksander Wennersteen
- Doug Oucharek
- Hiroshi Horii

# Executive Summary

The meeting focused on operational data, monitoring, analytics, and standardization requirements for the emerging Quantum Resource Interface (QRI) ecosystem. The primary presentation was delivered by Tim Osborne, who described how Oak Ridge National Laboratory (ORNL) collects, stores, visualizes, and analyzes operational data for Frontier and other HPC systems.

A key theme was that HPC operational monitoring evolved organically without standards, making cross-site and cross-vendor data comparison difficult. Participants agreed that the quantum ecosystem has a unique opportunity to establish common operational data definitions and interfaces early, before fragmentation occurs.

The discussion also explored:

- User personas and operational use cases for quantum telemetry.
- What information should and should not be exposed through QRI/QDMI/QRMI interfaces.
- The distinction between scheduling/accounting information and deep observability data.
- The need for vendor-neutral metrics and identifiers that can correlate jobs, workflows, and operational telemetry.
- Potential engagement with the HPC Operational Data Analytics community and workshop at SC.

The group agreed that future work should focus on identifying personas, defining minimal common data requirements, and understanding how existing interfaces (QMI, QDMI, QFW) can support these needs.

---

# Key Highlights

## 1. ORNL Analytics Architecture Overview

Tim Osborne described ORNL's operational analytics pipeline:

- Data collected from systems, storage, Slurm, telemetry sources, and users.
- Data ingested through Kafka as a common message bus.
- Data stored in Victoria Metrics, Druid, Elasticsearch, and MinIO.
- Grafana dashboards provide visualization.
- MinIO/Parquet archives support long-term research and analytics.

ORNL currently processes approximately 4 TB of operational data per day through Kafka.

---

## 2. Standardization Opportunity for Quantum Systems

A major discussion point was that HPC monitoring evolved without standards, creating interoperability challenges.

Key concern:

> Quantum systems can avoid repeating HPC's fragmentation by defining common operational data schemas early.

Benefits discussed:

- Cross-vendor comparison
- Cross-site comparison
- AI/ML analysis across datasets
- Common visualization and analytics tools
- Easier integration with workload managers and schedulers

---

## 3. Importance of User Personas

Multiple speakers emphasized that standards should be driven by users and use cases rather than technology.

Identified consumer groups include:

- Operations teams
- User support teams
- Researchers
- Accounting/allocation teams
- Workflow managers
- Scheduler developers
- Hardware vendors
- Quantum users and application developers

The group agreed that persona definition should likely be an early activity for the workstream.

---

## 4. Interface Scope Discussion

Several participants stressed that QRI/QDMI should avoid becoming a catch-all telemetry layer.

Key viewpoints:

### Matthias Traube

- Interfaces should focus on standardized machine information exposure.
- Data transport, storage, streaming, and analytics systems should remain separate architectural concerns.

### Aleksander Wennersteen

- Different data consumers need different data at different times.
- Some metrics are useful only for operators and vendors, not end users.

### Greg Arteen

- Resource interfaces should primarily support scheduling and workload-management decisions.
- Not all operational telemetry belongs in scheduler-facing interfaces.

---

## 5. Vendor Diversity and Telemetry Challenges

Participants observed significant differences among quantum vendors.

Example provided by Michael Sandoval:

- Superconducting vendors such as IBM and IQM expose substantial machine health and calibration information.
- Some ion-trap vendors expose much less operational information to users.

This reinforces the importance of defining a common abstraction layer rather than relying entirely on vendor-specific telemetry.

---

## 6. Unique Identifiers and Correlation

Woong Shin highlighted the value of carrying common identifiers throughout the stack.

Examples:

- Job IDs
- Workflow IDs
- Campaign IDs

This would allow downstream analytics systems to correlate:

- Operational telemetry
- Environmental data
- User workloads
- Scientific outcomes

---

## 7. ORNL IQM Deployment as a Learning Platform

ORNL's newly deployed IQM system was discussed as an early opportunity to gather practical lessons around:

- Vendor telemetry
- Grafana dashboards
- Monitoring integration
- Operational data models

However, participants agreed it is still early in the acceptance process and premature to draw conclusions.

---

## Proposed Topics for the Next Meeting

1. Deep dive on current interface implementations:
    - QMI
    - QDMI
    - QFW
2. Discussion of how those interfaces can expose operational information needed by HPC centers.
3. Review and define user personas.
4. Begin milestone planning for the workstream.
5. Revisit lessons learned from ORNL's IQM deployment when sufficient operational experience is available.
