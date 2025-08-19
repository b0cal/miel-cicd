## Functional requirements
- Add a new service to honeypot
  - With the help of configuration files
  - Match a certain docker image for the new service that will then be used to simulate the service
- Identify the scan/attack type
- Locate the origin of the attack (IP, etc.)
- Return logical responses to retain the attacker
  - When scanning, returning up port (if service is managed)
  - Then give access to the ressource (service should be available in other words)
- Record and store attacker interactions live
  - Capture payloads and IoCs
- App should always have a container up for every service it manages to diminish the attacker waiting time 
(- Filter known ip ranges)
- Remove a service
  - Once the attacker is out, container should be sanitized (removed and created again), to garantee a stable environment
- Handle honeypot general configuration via CLI

## Non-functional requirements
- Ressource access time should be ... s for the attacker
- Store logging in a SQLite
- Documenting the process of adding a service
  - Formalize configuration files
- There can be ... requests/s max
- Modular and testable code
- Automated tests on the code (unit, integration, etc.)
( - Dev. a lib that will be used by the binary (this should probably be in the workflow elicitation))
- API documentation
