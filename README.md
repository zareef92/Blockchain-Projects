# Title: Intercompany data contracts

## Background

Data quality issues are common in large banks - business lines such as Finance often rely on core data producers (e.g., Risk, Operations or IT) within the the group to provide them with data they need to operate effectively (e.g., to support regulatory reporting). However, due to inadequate data governance (in particular, existence of accountablity gaps, and lack of enforcement mechanisms) the quality of data they receive is often poor.

This can be solved by creating an internal market for the data services, where data can be priced, sold as a service, and where providers are remunerated for the quality of the service (i.e., data) they provide - much like high level services provisioned by shared service centres (such as IT) are managed in large banks. The anticipation of adequate remuneration can encourage the data producers to ensure they adhere closely to the service requirements, and in doing so, improve data quality. 

For markets to function effectively, theses services need to be governed by data contracts that stipulate what services the data producers are expected to provide, and reward or penalise them for the quality of the service. However, given the scale and complexity that can exist in developing intercompany data service arrangements, the task of ensuring that the terms of contract are adhered to can itself generate large administrative overheads that impact a number of support functions including Legal, Finance, IT -  this is unless the enforcement of those contracts can can be automated, and the rules used automate can be checked easily. Subsequently, this demands that:
1) Enforcement be managed by a set of automatable "smart data contracts" which lay out the terms of the agreement (including the service that exists between data producers and consumers, and the rewards or penalties that apply to the producer), and enforce those terms autonomously
2) The contracts are persisted in a tamper proof database (e.g, a blockchain) accessible to relevant data producers and consumers; this allows parties to check the terms of the services and the accuracy of rewards/penalties generated (in presence of any future disputes) with minimal friction, and without  manual interventions from support functions that otherwise would have to develop costly processes (e.g., reconciliation checks) to manage the contracts 

This document focuses on developing requirements for the developing smart data contract templates that can improve data quality (1).

## Design

Each contracts is characterised by a string of variables and functions:
- Variables store contract details, details of services provided, and updated account balances for the data producer and consumer after the services are rendered. 
- Contract is supported by 3 key functions which allow the producers to agree to the terms of the contract, acklowledge receipt of service received, and generate updated balances after the service is checked against the contract.

Detailed definitions for these variables and functions are shared below. 

### Variables:

- Service Contract Component
  - Contract ID: Unique ID for the contract  
  - Data Consumer: Address of the business divsion that is expected to receive the data service; addresses are also mapped to an account balance which stores the amount of money balance owned by the consumer/producer at any point in time 
  - Data Producer: Address of business division that is expected to produce the data service; addresses are also mapped to an account balance which stores the amount of money balance owned by the consumer/producer at any point in time
  - Data Service: The service that is expected to be provided by the producer the consumer e.g., a most basic form of this service can involve making sure the service provider adheres to an pre-agreed data schema
  - Service Start Date: Dates between which contractual agreements between producer and consumer begin
  - Service End Date: Dates between which contractual agreements between producer and consumer end
  - Service Reward: Rule for calculating rewards that applies when terms of service are adhered to - rewards  are expected to be denominated in a currency preferred by producer and consumer
  - Service Penalty: Rule for calculating penalties that apply when terms of service are not adhered to - penalties are expected to be denominated in a currency preferred by producer and consumer
  - Contract State: Status of contract - this is a dynamic variable for tracking if parties endorse the contract; status remains "Unsigned" by default until both parties digitally sign the contract, in which case the status changes to "Signed"

- Service Provision Component
  - Service ID: Unique ID for each service instance rendered by producer; a contract can have multiple service instances
  - Service Provision: Actual data service shared by producer with consumer as per contractual agreements, for a particular service instance
  - Service Date: Date on which service is provided
  - Service State: Status of the service -  this is a dynamic variable for tracking 2 flows:
      1. If producer "signs off" on the delivery of the service, and if consumer acknowledges this; status remains "Null" until both parties agree to endorse the service with their digital signature, in which case status changes to "Signed"  
      2. If the service relayed by producer meets the terms of the agreement, in which case status further changes to "Valid", not, in which case status changes to "invalid"  

- Service Validation Component
  - Producer Account Balance: Producer's account balance - this is a dynamic variable that is updated with net remuneration (the net of rewards - penalties is added to the balance) every time a service instance is deliver and the "check contract" function is triggered 
  - Consumer Account Balance: Consumer's account balance - this is a dynamic variable that is updated with net remuneration (the net of rewards - penalties is deducted from the balance) every time a service instance is deliver and the "check contract" function is triggered 
  
### Functions:
 - Sign Contract: Allows Data Producer and Data Consumer to endorse the terms relayed in contract with their digital signature (in particular, data service expected, contractual dates, rewards and penalties) 
 - Sign Service: Allows Data Producer and Data Consumer to acknowledge the deliver of a service instance
- Check Contract: Checks if service provision is in line with the data service agreemenet, calculates rewards/penalties, and updates consumers and producer's account balance - automatically triggered once the Sign Service Function is triggered

## Flow:
A high level workflow for detailing evoolution of contractual and states is detailed below:
1. Data Producer and Consumer review the terms of the contract and endorse it with their digital signature - this updates the Contract State to "Signed"
2. Data Producer submits the service to the contract

## Rationale
[A discussion of alternate approaches and the trade offs, advantages, and disadvantages of the specified approach.]

**Centralisation**

[A description of the steps in the implementation.]

## Open issues 
- Source data for variables declared in the contract would need appropriate control mechanisms to ensure they are received from a legitimate source or are supported by a consistent methodology, and cannot be changed in an unauthorised manner 
- Data services can only include data that is be known in advance 
- Persistence of contracts in a blockchain will yield greater benefits, but will implementation considerations in an enterprise environment will require careful review of existing data models and system requirements

-  
