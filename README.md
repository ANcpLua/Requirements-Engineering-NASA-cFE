# Requirements Engineering Compensation Exercise – NASA cFE

Missed unit (17 September 2025): Requirements Elicitation and Structuring — creativity lenses, positive vs. negative
requirements, use cases, and requirements rationale. Requirements source: NASA Core Flight Executive Software
Requirements Specification (version 5.1, 2017) at <https://github.com/nasa/cFE/blob/main/docs/cfe%20requirements.docx>.

---

## Glossary

| Term          | Meaning                                                                  |
|---------------|--------------------------------------------------------------------------|
| cFE           | Core Flight Executive, NASA's reusable flight software executive.        |
| SSRx          | Requirement identifier from the cFE Software Requirements Specification. |
| Event Message | Message placed on the cFE Software Bus to report status or errors.       |
| MET           | Mission Elapsed Time.                                                    |
| STCF          | Standard Time Correlation Factor used to convert MET to TAI/UTC.         |
| TAI / UTC     | International Atomic Time / Coordinated Universal Time.                  |

---

## Step 1 – Requirements gathered from the cFE SRS

**Note**: Requirements below are exact quotes from NASA cFE Software Requirements Specification (version 5.1, 2017).
SSR6 appears incomplete in the source document.

| ID    | Requirement (exact text from NASA document)                                                                                                                                        |
|-------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SSR1  | The cFE shall provide the capability to perform a startup of the cFE on power-on reset, processor reset and by command.                                                            |
| SSR2  | The cFE shall provide the capability to add a new application without recompiling all of the FSW.                                                                                  |
| SSR3  | The cFE shall provide the capability to control cFE Applications including starting, stopping, suspending and resuming the cFE Applications.                                       |
| SSR4  | The cFE shall provide the capability to use a flight software patch made to volatile memory.                                                                                       |
| SSR5  | The cFE shall provide the capability to use a flight software patch made to non-volatile memory.                                                                                   |
| SSR6  | The cFE shall provide the capability to [INCOMPLETE IN SOURCE]                                                                                                                     |
| SSR7  | The cFE shall provide a <MISSION_DEFINED> selection that determines whether the cFE is configured to function as a time server or time client.                                     |
| SSR8  | The cFE shall provide a <MISSION_DEFINED> selection of which time format (TAI or UTC) is used as the default time representation.                                                  |
| SSR9  | The cFE shall compute TAI and UTC as follows: TAI = MET + STCF; UTC = MET + STCF – Leap Seconds.                                                                                   |
| SSR10 | The cFE shall preserve the STCF, Leap Seconds and Time Status values in a <MISSION_DEFINED> Critical Data Store.                                                                   |
| SSR11 | The cFE shall provide an interface for other cFE components and Applications to query spacecraft time.                                                                             |
| SSR12 | The cFE shall provide an interface for other cFE components and Applications to send Event Messages on the Software Bus and optionally to an Event Message Port.                   |
| SSR13 | The cFE shall classify Event Messages according to their Event Type (diagnostic, informational, critical, etc.) as defined in the cFE Application Developer's Guide.               |
| SSR14 | The cFE shall provide an Event Message filtering mechanism with Commands for enabling/disabling filters.                                                                           |
| SSR15 | The cFE shall provide an Application interface for registering an application to use cFE event services along with registering that applications filtered events and filter masks. |

---

## Step 2 – Problems, methods, and exercises from the missed unit

| Type     | Description                                                                      | Source                                                                                                                                                                                                         |
|----------|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Method   | Structuring functional requirements by domain object and use case                | [Requirements Structuring.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Requirements%20Structuring.pdf), slides 42, 49, 51                                                  |
| Exercise | Positive vs. negative requirements (burglar alarm example)                       | [Requirements Structuring.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Requirements%20Structuring.pdf), slides 35, 38                                                      |
| Method   | Creativity lenses for excitement requirements: Combination, Variation, Inversion | [Extended Slidedeck Requirements Elicitation.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Extended%20Slidedeck%20Requirements%20Elicitation.pdf), slides 76-85             |
| Exercise | Home exercise "three exciting goggles features"                                  | [Home Exercise - Eliciting Excitement Requirements.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Home%20Exercise%20-%20Eliciting%20Excitement%20Requirements.pdf), slide 87 |
| Method   | Requirements rationale ("Why do you have this requirement?")                     | [Extended Slidedeck Requirements Elicitation.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Extended%20Slidedeck%20Requirements%20Elicitation.pdf), slides 97-105            |

---

## Step 3 – Applying the missed content to NASA cFE

### 3.1 Method – Structuring by domain object and use case ([Requirements Structuring.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Requirements%20Structuring.pdf), slides 42, 49, 51)

**Note**: SSR6 is omitted from analysis as it is incomplete in the NASA source document.

**Manual attempt (no AI)**
Domain objects: Application, Time Service, Event Service, Critical Data Store, Software Bus.

Application:

- Start Application (SSR1, SSR3)
- Stop Application (SSR3)
- Add Application (SSR2)
- Apply Patch (SSR4, SSR5)

Time Service:

- Configure Time Mode (SSR7)
- Configure Time Format (SSR8)
- Compute Time (SSR9)
- Query Time (SSR11)
- Preserve Time Data (SSR10)

Event Service:

- Send Event Message (SSR12)
- Classify Event (SSR13)
- Filter Event (SSR14, SSR15)

**Baseline AI prompt**

```
Organize the NASA cFE requirements SSR1–SSR15 (excluding SSR6 which is incomplete) by domain object and use case. List each domain object, then list the use cases under it with the relevant SSR IDs. Use the exact requirement text from the NASA document.
```

**Baseline AI output**

Application Management:

- Start/Restart Application: SSR1
- Add Application: SSR2
- Control Application Lifecycle: SSR3
- Apply Patch from Volatile Memory: SSR4
- Apply Patch from Non-Volatile Memory: SSR5

Time Services:

- Select Time Server/Client Mode: SSR7
- Select Time Format: SSR8
- Compute TAI/UTC: SSR9
- Query Time: SSR11
- Store Time Configuration: SSR10

Event Services:

- Send Event Message: SSR12
- Classify Event Type: SSR13
- Filter Events: SSR14
- Register for Event Services: SSR15

**Improved AI prompt**

```
Create a table with columns (Domain Object, Use Case, SSR IDs, Business Value). Organize the NASA cFE requirements SSR1–SSR15 (excluding SSR6 which is incomplete in the source) by domain object and use case. For each use case, explain the business value in 1 sentence based on the exact requirement text.
```

| Domain Object | Use Case                      | SSR IDs | Business Value                                                      |
|---------------|-------------------------------|---------|---------------------------------------------------------------------|
| Application   | Start Application             | SSR1    | Ensures system initialization after reset or commanded restart.     |
| Application   | Add Application               | SSR2    | Enables dynamic software updates without full system recompilation. |
| Application   | Control Application Lifecycle | SSR3    | Provides operational flexibility to manage running applications.    |
| Application   | Apply Volatile Patch          | SSR4    | Supports temporary software fixes in RAM for testing.               |
| Application   | Apply Non-Volatile Patch      | SSR5    | Enables persistent software updates across reboots.                 |
| Time Service  | Configure Time Mode           | SSR7    | Adapts cFE to mission-specific time synchronization architecture.   |
| Time Service  | Configure Time Format         | SSR8    | Matches mission requirements for TAI or UTC time representation.    |
| Time Service  | Compute Time                  | SSR9    | Provides accurate mission time calculations for all components.     |
| Time Service  | Preserve Time Data            | SSR10   | Ensures time continuity across system resets.                       |
| Time Service  | Query Time                    | SSR11   | Allows components to access current spacecraft time.                |
| Event Service | Send Event Message            | SSR12   | Enables status and error reporting across the software bus.         |
| Event Service | Classify Event                | SSR13   | Supports priority-based event handling and filtering.               |
| Event Service | Filter Event                  | SSR14   | Reduces event message volume based on operator preferences.         |
| Event Service | Register for Events           | SSR15   | Allows components to subscribe to relevant event streams.           |

---

### 3.2 Exercise – Positive vs. negative requirements ([Requirements Structuring.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Requirements%20Structuring.pdf), slides 35, 38)

**Note**: SSR6 is omitted from analysis as it is incomplete in the NASA source document.

**Manual attempt (no AI)**
Positive: cFE shall emit a CRITICAL Event Message when an application exceeds its CPU budget.
Negative: cFE shall not restart an application automatically if the mission has flagged it as exempt from auto-restart.

**Baseline AI prompt**

```
Using the exact NASA cFE requirements SSR1–SSR15 (excluding SSR6 which is incomplete), provide one positive requirement (what cFE must do) and one negative requirement (what it must avoid). Keep explanations brief.
```

**Baseline AI output**
Positive: cFE must send an Event Message to the Software Bus when an application state changes (based on SSR12, SSR13).
Negative: cFE must not apply a patch from non-volatile memory if the patch signature verification fails (extension of
SSR5).

**Improved AI prompt**

```
Create a table with columns (Requirement ID, Type [Positive/Negative], Requirement text, Verification target, Referenced SSRs). Base each requirement on the exact NASA cFE requirements SSR1–SSR15 (excluding SSR6 which is incomplete) and ensure the statement is testable.
```

| Requirement ID | Type     | Requirement text                                                                                                                         | Verification target                                                                         | Referenced SSRs    |
|----------------|----------|------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|--------------------|
| PR-01          | Positive | cFE shall emit a CRITICAL Event Message and increment the invalid-command counter when an application exceeds its configured CPU budget. | Event raised within 1 s of the budget breach; counter increments exactly once per incident. | SSR3, SSR12, SSR13 |
| NR-01          | Negative | cFE shall not automatically restart an application that the mission has marked as "manual recovery only."                                | During tests, flagged applications remain stopped after fault injection in 100 % of cases.  | SSR3               |

---

### 3.3 Method – Creativity lenses ([Extended Slidedeck Requirements Elicitation.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Extended%20Slidedeck%20Requirements%20Elicitation.pdf), slides 76-85)

**Note**: SSR6 is omitted from analysis as it is incomplete in the NASA source document.

**Manual attempt (no AI)**
Combination: Patches + time services → simulate patch impact on time servers/clients before activation.
Variation: Named mission scenes that change filters and control defaults automatically.
Inversion: System pushes an orbit recap highlighting unusual Event Message patterns and time-status changes.

**Baseline AI prompt**

```
Using the exact NASA cFE requirements SSR1–SSR15 (excluding SSR6 which is incomplete), suggest three excitement requirements via Combination, Variation, and Inversion. Keep the answers short.
```

**Baseline AI output**
Combination: Merge patch validation with event filtering to auto-test patches against current event configurations.
Variation: Provide voice-command interface for application control instead of traditional commands.
Inversion: Instead of operators querying time status, push automated time anomaly alerts when STCF drift exceeds
threshold.

**Improved AI prompt**

```
Produce a table with columns (Requirement ID, Lens, Requirement text, Verification target, Referenced SSRs). Each requirement must be testable (include a quantitative target) and cite the exact NASA cFE requirements SSR1–SSR15 (excluding SSR6 which is incomplete) that it extends. Use Combination, Variation, and Inversion exactly once each.
```

| Requirement ID | Lens        | Requirement text                                                                                                                            | Verification target                                                                             | Referenced SSRs                  |
|----------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|----------------------------------|
| ER-01          | Combination | Before any uploaded patch becomes active, cFE runs a sandbox simulation showing its impact on every configured time server and time client. | Simulation finishes within 60 s and detects ≥95 % of drift issues identified during validation. | SSR4, SSR5, SSR7–SSR11 (no SSR6) |
| ER-02          | Variation   | Named "mission scenes" (launch, orbit, eclipse) instantly switch the active Event Message filters and application-control defaults.         | Scene change completes within 5 s and reuses ≥90 % of preapproved filter configurations.        | SSR3, SSR13, SSR14               |
| ER-03          | Inversion   | After each orbit, cFE automatically sends a recap highlighting unusual Event Message patterns together with time-status changes.            | Recap arrives within 5 min of orbit end and covers ≥90 % of anomalies detected in trials.       | SSR10, SSR12, SSR13              |

---

### 3.4 Method – Requirements rationale ([Extended Slidedeck Requirements Elicitation.pdf](https://github.com/ANcpLua/Requirements-Engineering-NASA-cFE/blob/main/docs/Extended%20Slidedeck%20Requirements%20Elicitation.pdf), slides 97-105)

**Note**: SSR6 is omitted from analysis as it is incomplete in the NASA source document.

**Manual attempt (no AI)**
Analyzed SSR7: "The cFE shall provide a <MISSION_DEFINED> selection that determines whether the cFE is configured to
function as a time server or time client."
Rationale question: Why does the mission need to choose time server vs. client mode?
Underlying need: Different spacecraft have different time synchronization architectures (some receive time from ground,
some from GPS, some from other spacecraft).
Rewritten: cFE shall support both time server mode (providing authoritative time) and time client mode (synchronizing to
external time source), selectable via configuration table entry.

**Baseline AI prompt**

```
For SSR7 (exact text: "The cFE shall provide a <MISSION_DEFINED> selection that determines whether the cFE is configured to function as a time server or time client."), apply requirements rationale questioning. Ask "Why?" at least three times to uncover the underlying need. Provide the chain of rationale.
```

**Baseline AI output**
SSR7: Mission-defined setting selects time server/client mode.
Why? Different missions have different time architectures.
Why? Some spacecraft receive authoritative time from ground stations, others from onboard atomic clocks, others from
GPS.
Why does this matter? Using wrong time mode could cause time synchronization failures across the spacecraft.
Underlying need: Flexible time architecture that adapts to mission-specific time sources and distribution topology.

**Improved AI prompt**

```
Create a table with columns (Original SSR, Rationale Chain [Why 1, Why 2, Why 3], Underlying Need, Improved Requirement Text). Apply requirements rationale to SSR7, SSR8, and SSR14 using their exact text from the NASA document. For each, ask "Why?" at least three times.
```

| Original SSR                                                                                                                                         | Rationale Chain                                                                                                                                                    | Underlying Need                                                                                  | Improved Requirement Text                                                                                                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SSR7: The cFE shall provide a <MISSION_DEFINED> selection that determines whether the cFE is configured to function as a time server or time client. | Why? Different missions have different time topologies. Why? Time sources vary (ground, GPS, atomic clock). Why does this matter? Wrong mode causes sync failures. | Flexible time architecture supporting multiple synchronization topologies                        | cFE shall support both time server mode (providing authoritative MET/STCF to other components) and time client mode (synchronizing MET/STCF from external source), with mode selection via Mission Configuration Table entry that specifies time source type and update frequency. |
| SSR8: The cFE shall provide a <MISSION_DEFINED> selection of which time format (TAI or UTC) is used as the default time representation.              | Why? Some payloads require TAI, others UTC. Why? Leap-second handling differs. Why does this matter? Time format mismatch causes payload data correlation errors.  | Support for both leap-second-aware (UTC) and continuous (TAI) time representations               | cFE shall provide both TAI (continuous) and UTC (leap-second adjusted) time formats, with default format selectable via configuration and runtime conversion API available to all components.                                                                                      |
| SSR14: The cFE shall provide an Event Message filtering mechanism with Commands for enabling/disabling filters.                                      | Why? Reduce event message volume. Why? Operators get overwhelmed. Why does this matter? Critical events missed in noise.                                           | Adaptive event filtering that highlights critical information while suppressing routine messages | cFE shall provide configurable event filters supporting rate-limiting (max N events per minute), severity-based filtering (by event type), and source-based filtering (by application ID), with filter rules loadable via command table and persistent across resets.              |
