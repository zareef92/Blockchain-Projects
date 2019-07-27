# Title: Intercompany data contracts

## Background

Data quality issues are common in large banks - business lines such as Finance often rely on core data producers (e.g., Risk, Operations or IT) within the the group to provide them with data they need to operate effectively (e.g., to support regulatory reporting), but due to inadequate data governance (in particular, existence of accountablity gaps, and lack of enforcement mechanisms) the quality of data they receive is often poor.

This can be solved by creating an internal market for the data services, where data can be priced, sold as a service, and where providers are remunerated for the quality of the service (i.e., data) they provide - much like high level services provisioned by shared service centres (such as IT) are managed in large banks. The anticipation of adequate remuneration will encourage the data producers to ensure they adhere closely to the service requirements, and in doing so, improve data quality. 

For markets to function effectively, theses services need to be governed by data contracts that stipulate what services the data producers are expected to provide, and reward or penalise them for the quality of the service. However, given the scale and complexity that can exist in developing intercompany data service arrangements, the task of ensuring that the terms of contract are adhered to can itself generate large administrative overheads that impact a number of support functions including Legal, Finance, IT -  this is unless the enforcement of those contracts can can be automated, and the rules used automate can be checked easily. Subsequently, this demands that:
- enforcement be managed by a set of automatable "smart data contracts" which lay out the terms of the agreement (including the service that exists between data producers and consumers, and the rewards or penalties that apply to the producer), and enforce those terms autonomously
- the contracts are persisted in a tamper proof database (e.g, a blockchain) accessible to relevant data producers and consumers; this allows parties to check the terms of the services and the accuracy of rewards/penalties generated (in presence of any future disputes) with minimal friction, and without  manual interventions from support functions that otherwise would have to develop costly processes (e.g., reconciliation checks) to manage the contracts 

This document lays out requirements for the developing smart data contract templates.


## Design

Developing and enforcing data service contracts require development of three independent contract templates:
- Service Contract: Stipulate the rules that are being agreed between data producers and consumers in advance 
- Provision Contract: Delivers the data service from producer to consumer 
- Validation Contract: Checks that the data service relayed in Provision Contract is in line with Service Contract, and calculates any rewards and penalties

### Service contract

Variables:
- Data Consumer: Business divsion that is expected to receive the data, and remunerate the data producer based on the quality of service they provide.
- Data Producer: Business division that is expected to produce the data, and receive renumeration in exchange for the service they provide
- Data Service: The service against that is expected to be provided by the producer the consumer - a most basic form of this service can involve making sure the service provider adheres to an pre-agreed data schema
- Service Reward: Rewards that applies hen terms of service are adhered to
  - Rewards can be denominated in units of account local to the system (e.g., Ether) or conventional currencies (e.g. USD)
  - Rewards will be conditional on the validation performed against Data Service.
- Service Penalty - Penalties that apply when terms of service are not adhered to 

Service provision 
- Data Consumer: 
- Data Producer:
- Data Service:
Service validation contract

### Service contract
- In the contract template, data consumer, producer are also identified by their public key, which ensures the 


[A discussion of alternate approaches and the trade offs, advantages, and disadvantages of the specified approach.]
**Centralisation**


## Implementation

[A description of the steps in the implementation.]

## Open issues (if applicable)

[A discussion of issues relating to this proposal for which the author does not
know the solution. This section may be omitted if there are none.]

