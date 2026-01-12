Containerization for Environment Consistency

Docker was used to package the FHIR server along with all its dependencies into a single container image. This eliminated dependency and configuration conflicts across different student systems, ensuring that every participant ran an identical environment regardless of operating system or hardware. As a result, setup was reproducible, onboarding time was reduced, and “it works on my machine” issues were completely avoided.

Preservation of Clinical Semantics

To eliminate ambiguity caused by inconsistent or locally defined values in the RMHC CSV data (such as gender abbreviations), the project implemented a FHIR ConceptMap and leveraged the $translate operation. This approach systematically converted source values into standardized codes with explicit meaning, ensuring semantic accuracy, maintaining clinical integrity, and enabling true interoperability across systems.

Atomic and Reliable Data Transactions

FHIR Transaction Bundles were used to upload Patient and Observation resources as a single atomic operation rather than individual requests. Temporary UUID references linked related resources within the bundle, ensuring that either all resources were successfully created or none were committed. This prevented partial data persistence, avoided orphaned clinical records, and preserved referential integrity within the system.
