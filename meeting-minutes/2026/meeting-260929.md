# QRI Workstream Meeting Summary 260929

## Attendees

- Yoonho Park
- Eun Kyung Lee
- HIROSHI Horii
- Claudio Carvalho
- Doug Oucharek
- Matthias Traube
- Patrick Hopf
- Marcel Walter
- Aleksander Wennersteen
- Andrea Casotto
- Oscar Wallis
- Gabor Samu

---

# Agenda

1. SC / OpenQSC demonstration planning
2. QRI, QRMI, and QDMI alignment with demonstration requirements
3. Backplane / SpaceRT discussion
4. QFW progress update
5. QDMI support for IBM Quantum
6. Future architectural enhancements
7. Resource reservation and scheduling requirements
8. Milestone review

---

# Discussion

## SC Demonstration Planning

The group reviewed the proposed architecture for the OpenQSC / SC demonstration. The architecture includes:

- Qiskit
- PennyLane
- MQT Core
- QFW
- Workflow engines (e.g. StreamFlow, Prefect)
- Slurm
- QRI
- QRMI
- QDMI

The team agreed that the current QRI/QRMI/QDMI roadmap is largely aligned with demonstration requirements and no major redesign appears necessary at this stage.

Additional users and deployment environments associated with the SC demonstration may help expose gaps and usability concerns that are not currently visible.

## Backplane / SpaceRT

The group discussed AMD's Backplane / SpaceRT effort and how it relates to the QRI architecture.

Topics discussed included:

- Relationship to QRMI and QDMI
- Potential low-latency quantum-classical integration models
- Similarities with NVIDIA and AMD accelerator integration approaches
- Possible implications for future quantum error correction workflows

The group agreed that additional technical discussion with the Backplane team would be valuable before drawing architectural conclusions.

## Candidate Demonstration Workloads

Several candidate workloads were discussed for the SC demonstration:

- Auxiliary-field quantum Monte Carlo workflow presented during Quantum Week
- Existing AWS collaboration examples
- Quantum chemistry workflows already present in the QDMI repository
- Hybrid quantum-classical applications running through QDMI

The group agreed that existing hybrid workloads provide strong demonstration candidates.

## QDMI IBM Backend Progress

The MQT team reported substantial progress on IBM Quantum support through QDMI.

Highlights:

- IBM backend implementation is nearing completion
- Existing repository and documentation are available
- Hybrid workflow execution has been demonstrated successfully
- Completion is expected within weeks rather than months

## QFW Progress Update

Doug provided an update on recent QFW development activities.

### New Features

- IBM Quantum support
- OpenQASM 2 support
- QPY support
- Compressed QPY (QPY + GZIP) support

### Performance Improvements

- Significant circuit size reduction through compressed QPY
- Improved job cancellation support
- Resolution of credential and key-management race conditions

### RPC Improvements

A prototype based on Mercury/Margo has been developed and demonstrates significantly improved performance compared to the current implementation.

### Telemetry

Work continues on telemetry and dashboard support for:

- Demonstration visibility
- Monitoring
- Performance analysis

## IBM Quantum Integration (PR #69)

A new pull request adds IBM Quantum support to the QFW RunCircuit operation.

Capabilities include:

- QPY loading
- Backend selection
- Circuit compilation
- Payload generation
- Job execution
- Result normalization

Additional support was added for:

- Circuit parameter values
- Compilation options

## Compilation and Execution Separation

A proposal was discussed to separate:

1. Circuit compilation
2. Circuit execution

into independent jobs.

Potential benefits include:

- Better scheduler utilization
- Reduced QPU idle time
- Improved workflow composition
- Better support for heterogeneous systems

The proposal was viewed positively but is not required for the SC demonstration timeline.

## Resource Reservations

The group discussed future requirements around resource reservation and scheduling.

Topics included:

- Holding reservations across workflow stages
- Scheduler integration
- Reservation APIs

Current IQM reservations are primarily UI-driven. Future support is expected through the planned iteration mode capability.

## API Stability

Concerns were raised regarding changes in IQM API behavior occurring without corresponding version changes.

The group noted the importance of:

- Improved regression testing
- Earlier access to production-like environments
- Stronger compatibility validation procedures

## Milestone Review

The group confirmed successful execution of the following workflow:

```text
Qiskit -> Slurm -> QRI -> Simulator
