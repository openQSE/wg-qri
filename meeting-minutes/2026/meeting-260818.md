# QRMI and QDMI Comparative Analysis and Implications for the Quantum Resource Interface (QRI) Specification

---

# Executive Summary

The OpenQSE QRI Workstream reviewed Doug's comparative analysis of QRMI and QDMI as a foundational step toward defining a standardized Quantum Resource Interface (QRI). The analysis demonstrated that QRMI, QDMI, and direct IQM access all produced equivalent functional results, successfully identifying the same hardware topology and generating identical quantum execution outputs. As a result, the discussion shifted away from correctness and focused on architectural differences, capability gaps, scheduling considerations, and standardization requirements.

A recurring theme throughout the meeting was that many observed limitations are not defects in either library but are instead reflections of the current maturity level of quantum provider ecosystems. Participants discussed capability discovery, reservation semantics, scheduler integration, accounting information, authentication mechanisms, queue visibility, and portability. The group generally aligned on using these findings to guide development of a vendor-neutral QRI specification that can influence both interface implementations and future provider capabilities.

---

# Highlights

## 1. Functional Equivalence Validated

Doug's testing compared:

- QRMI
- QDMI
- Direct IQM access

Key findings:

- All approaches discovered the same IQM topology (20 qubits, 30 edges).
- All produced identical execution results for test circuits.
- All results normalized successfully into the common QHW Result v1 format.

### Takeaway

The libraries are functionally comparable, enabling future discussions to focus on usability, portability, and interface design rather than correctness.

---

## 2. Different Architectural Philosophies

### QRMI

- Resource-centric design.
- Vendor implementations are integrated into a single library.
- More naturally aligned with scheduler and resource-management perspectives.

### QDMI

- Device-centric design.
- Vendors provide separate plug-ins built against a stable ABI.
- More naturally aligned with hardware abstraction.

### Takeaway

The distinction represents a design choice rather than a deficiency in either approach.

---

## 3. Capability Discovery Gap

A key shortcoming identified was the inability to easily determine:

- Supported operations
- Device capabilities
- Optional provider features

Current behavior:

| Library | Behavior |
|----------|-----------|
| QRMI | Unsupported properties may return null values |
| QDMI | Unsupported operations return "not supported" |

Developers currently need to invoke functions to discover whether support exists. Doug suggested an approach similar to LibFabric capability hints or introspection APIs.

### Takeaway

A standardized capability-discovery mechanism should be considered for the QRI specification.

---

## 4. Reservations and Resource Locking

The group discussed the absence of a portable reservation/locking mechanism.

Key observations:

- QDMI currently has no reservation concept.
- QRMI includes acquire semantics but support varies by provider.
- IQM reservations exist but are not yet programmatically available.
- Most quantum providers do not currently expose API-level reservation capabilities.

Discussion emphasized that:

- Providers may need to evolve before true reservation support becomes practical.
- Libraries should at least provide explicit indication when reservation support is unavailable.

### Takeaway

Reservation semantics remain a major open topic for future QRI specification work.

---

## 5. The "Two Queue Problem"

One of the most important topics discussed was coordination between:

1. HPC scheduler queues
2. Quantum provider queues

Challenges include:

- Queue visibility
- Reservation coordination
- Priority propagation
- Resource prediction
- Scheduling accuracy across domains

Potential approaches discussed:

- Queue depth reporting
- Queue position reporting
- Reservation references
- Priority and deadline signaling
- Scheduler-to-provider feedback loops
- Broker or daemon-based mediation layers

### Takeaway

Resolving the two-queue problem may become one of the central objectives of the QRI specification effort.

---

## 6. Accounting and Timing Information

Doug highlighted that providers expose valuable accounting and timing information that is not consistently surfaced by current interfaces.

Examples:

- IQM provides seven execution timestamps.
- Timing information is often provider-specific.
- Calibration identifiers and execution metadata are not consistently exposed.

Challenges:

- Different quantum modalities may require different timestamp models.
- Portable accounting records require some degree of normalization.

### Takeaway

Standardized accounting records and timing metadata should be considered part of the future QRI specification.

---

## 7. Performance Observations

WAN-based startup measurements showed:

| Path | Startup Time |
|--------|-------------|
| QRMI | ~1.3s |
| Direct IQM | ~2.8s |
| QDMI | ~3.3s |

Subsequent discussion revealed:

- Connection pooling significantly impacts performance.
- Both libraries benefit from caching static data.
- QDMI connection-pooling improvements have already been implemented but not yet released.

### Takeaway

Connection pooling and caching represent important value-add features that should continue to be emphasized.

---

## 8. Error Handling Improvements

Doug identified a debugging issue where loss of connectivity caused QRMI to silently invalidate cached data rather than surfacing a clear error.

Effects included:

- Misleading device information
- Difficult debugging experiences
- Delayed fault discovery

Responses:

- OHTANI-san confirmed awareness of the issue.
- Logging improvements have already been implemented.
- Additional fixes are planned.

### Takeaway

Consistent and visible failure reporting should be part of future interface expectations.

---

## 9. Payload Standardization

Significant differences were observed in IQM JSON usage:

### QRMI

Treats IQM JSON as the entire run request.

### QDMI

Treats IQM JSON as only the circuit payload.

Discussion emphasized:

- Reducing vendor-specific formats.
- Avoiding dependence on proprietary payload structures.
- Leveraging formats such as OpenQASM and QIR where possible.

### Takeaway

The future specification should consider defining common payload expectations and preferred interchange formats.

---

## 10. Authentication and Secret Management

Participants discussed several authentication approaches:

- Environment variables
- Session parameters
- Secure credential stores
- Runtime memory-only handling of secrets

Amir described an implementation where user credentials are stored securely and injected only within service runtime memory rather than being exposed through shells or environments.

### Takeaway

Authentication and secret management likely require broader OpenQSE architectural guidance beyond QRMI and QDMI alone.

---

# Action Items

## Yonnho Park

- Distribute a summary of Doug's findings and proposed resolutions.
- Begin the next meeting with a review of issue-resolution proposals before returning to accounting-information discussions.

---

## Munetaka Ohtani

- Present QRMI accounting-information design at the next meeting.
- Share design rationale and gather community feedback.
- Continue development on reservation/acquire support and error-handling improvements.

---

## Lukas Burgholzer / QDMI Team

- Identify a presenter for QDMI accounting-information discussions at the next meeting.
- Continue integration of enhancements already identified through the comparison effort, including queue visibility and connection pooling improvements.

---

## QRI Specification Team

Evaluate and potentially standardize:

- Capability discovery mechanisms.
- Reservation and locking semantics.
- Two-queue coordination models.
- Queue visibility and scheduling feedback.
- Accounting and timing metadata.
- Calibration and execution provenance information.
- Authentication and secret-management guidance.
- Portable payload and circuit representation standards.

---

# Overall Assessment

The meeting successfully validated that both QRMI and QDMI achieve equivalent functional outcomes while identifying several important areas where a future QRI specification can add value. The most impactful discussions centered on capability discovery, accounting information, provider feedback mechanisms, queue coordination, reservation support, and portability. The workstream appears well positioned to transition from implementation comparisons toward defining the broader requirements and semantics of a standardized Quantum Resource Interface.
