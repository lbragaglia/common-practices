# Non-functional requirements specification

## Project
Briefly describe the system/component/flow to which this NFR spec applies.
* Type of component (event-driven, batch processing, web api, web application, …)
* Inputs/outputs (message flows, data sources, contracts, ...)
* Data storage (how internal/intermediate data is stored)
* Dependencies (external services, …)

May include a simple diagram of the components/flows if this document refers to the whole system.

# Resiliency and integrity
## Error handling and failure recovery
Describe the error policy approach (fail-fast or fail-safe) and how the errors are handled.
* Are permanent errors distinguished from transient?
* Are transient errors reprocessed and how (automatically or manual, live or off-line, …)?
* How are errors signaled or stored?
* Is there a fall-back action for persistent errors that cannot be recovered (parking to a dead-letter, ...)?

## Concurrency and consistency
Describe the transactional behaviour and the data integrity requirements.
* Is it a stateful or stateless system?
* Does the system support multiple concurrent execution?
* What kind of transactions are used, if supported by the resource managers (isolation, consistency level, …)?
* Is data integrity guaranteed by the storage systems?
* How multiple independent transactions are handled in case of failure (compensating actions, ...)?
* How invalid messages/calls are handled?
* How to out-of-order or poison messages are handled?

