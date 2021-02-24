# Non-functional requirements specification

## Project
Briefly describe the system/component/flow to which this NFR spec applies.
* Type of component (event-driven, batch processing, web api, web application, …)
* Inputs/outputs (message flows, data sources, contracts, …)
* Data storage (how internal/intermediate data is stored)
* Dependencies (external services, …)

May include a simple diagram of the components/flows if this document refers to the whole system.

## Resiliency and integrity
### Error handling and failure recovery
Describe the error policy approach (fail-fast or fail-safe) and how the errors are handled.
* Availability of the system in case of failures
* Are permanent errors distinguished from transient?
* Are transient errors reprocessed and how (automatically or manual, live or off-line, …)?
* How are errors signaled or stored?
* Is there a fall-back action for persistent errors that cannot be recovered (parking to a dead-letter, …)?

### Concurrency and consistency
Describe the transactional behaviour and the data integrity requirements.
* Is it a stateful or stateless system?
* Does the system support multiple concurrent execution (scalability, …)?
* What kind of transactions are used, if supported by the resource managers (isolation, consistency level, …)?
* Is data integrity guaranteed by the storage systems?
* How multiple independent transactions are handled in case of failure (compensating actions, …)?
* How invalid messages/calls are handled?
* How to out-of-order or poison messages are handled?

## Performance
Describe the key measures of speed and load that the system must support or guarantee (SLA). For each metrics try to specify different estimates: expected, max, peak, growth rate and scalability, degradation under overload, etc. Include also any other constraints that could impact performance.
### Metrics
* Capacity of the system (number of total entity handled)
* Throughput for each flow/api (number of transactions per time unit)
* Response time for each request or message processing (timespan)
* Resource utilization (size of memory/disk/cpu, network bandwidth)
* Latency for synchronous calls and data availability/freshness (near real-time, …)
### Risks
* Import/export/reporting operations (specify if they are isolated or how could impact live system)

## Delivery
Briefly describe how to deliver and operate on a running (production) system.
### Continuous delivery
* How the system is built, tested and deployed (environments/gates/steps, continuous delivery or deployment?)
* How to perform an upgrade or a rollback
* How to start/stop/disable/verify and configure a running system (feature flags, (build/deploy/run)-time configuration, environment configuration, …)
### Operations
* (runbook and on-call checklist)
* (backup and restore)

## Security
### Security
* access control and permissions
* how malicious messages/calls are detected and handled
* encrypted communication channels
### Privacy
* personal information data handling
* auditing of sensitive/critical actions

## Observability
Describe how a running (production) system can be monitored (low-level, the system is working flawless) and observed (hi-level, the system is doing what it is supposed to do).
### Monitoring
* Which logs and metrics are produced (log rotation policy, retention, …)
* Is there a way to perform distributed tracing (correlation-id, dyna-trace/x-ray, …)?
* How errors/alerts are collected/triggered
* Which dashboards are available (grafana, kibana, …)
### Observability
* Which domain KPI are monitored
* Which dashboards are available (grafana, kibana, …)

## Assumptions, constraints and risks
Describe any other issues that have an impact of the implementation of the solution but can not be included in previous sections.
* Expected or required behaviour of upstream data sources or service providers
* Corner case or other scenarios not supported or ignored and explain why
* Limits derived from technology/environment/practices handled by other teams
* Legal or internal policy restrictions

