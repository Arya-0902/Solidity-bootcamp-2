# Solidity-bootcamp-2

#Challenge (Second Task)

1. For now, our proposal just has a description but finding proposals with a description can be hard since they tend to be long. For that reason, we want our proposal to have a title too. Your job is to extend the Proposal structure to include a title field of type string.
2. This will allow each proposal to have a brief title in addition to its description
3. Submit your code below.

solution:

```sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract ProposalContract {

    struct Proposal {
        string title; // Title of the proposal
        string description; // Description of the proposal
        uint256 approve; // Number of approve votes
        uint256 reject; // Number of reject votes
        uint256 pass; // Number of pass votes
        uint256 total_vote_to_end; // When the total votes in the proposal reaches this limit, proposal ends
        bool current_state; // This shows the current state of the proposal, meaning whether if passes of fails
        bool is_active; // This shows if others can vote to our contract
    }

    mapping(uint256 => Proposal) proposal_history; // Recordings of previous proposals
}
```
