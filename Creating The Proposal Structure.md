What Are We Going To Build 

In this tutorial, we will be building a smart contract that allows the owner to create and manage proposals that other users can vote on. 
This is a simple voting system that can be used for various purposes, such as governance, decision making, or feedback. 
We will learn how to use structs, mappings, arrays, modifiers, and libraries to implement the logic of the proposal system. By the end of this tutorial, you will have a working proposal contract that you can customize and extend for your own needs.

What does Proposal Contract do:

 This contract is a simple voting system for proposals created by the owner.  
 In proposals, we have a description for the explanation of the proposal. We also have variables for holding numbers of approve, reject and pass votes. We also have couple of additional fields that helps us to track more information about our proposals. 
 The owner can create a new proposal with a description and a vote limit, and other users can vote to approve, reject or pass the proposal.  
 The contract calculates the current state of the proposal based on the number of votes, and ends the proposal when the vote limit is reached.  
 The contract also keeps a history of all the proposals and their outcomes, and prevents users from voting more than once. 
 The contract uses some modifiers to restrict access and check conditions, and some helper functions to implement the logic.
 

Starting to the Contract

Let's start with defining our contract:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;
contract ProposalContract {
    // Our contract code
}
```

Now that we have the basis for our contract, we can create our proposal structure.
To store the proposals, first we need to have a structure that has the necessary fields for our Proposal.

```
struct Proposal {
        string description; // Description of the proposal
        uint256 approve; // Number of approve votes
        uint256 reject; // Number of reject votes
        uint256 pass; // Number of pass votes
        uint256 total_vote_to_end; // When the total votes in the proposal reaches this limit, proposal ends
        bool current_state; // This shows the current state of the proposal, meaning whether if passes of fails
        bool is_active; // This shows if others can vote to our contract
}
```

Now that we have a necessary structure for our proposal but the question arises, how can we store them? The answer is using mapping.
```
mapping(uint256 => Proposal) proposal_history; // Recordings of previous proposals
```

In this mapping we have uint256 as the key and the proposal as the value. So, we will be able to get the proposal based on its key uint256 value, which will be the id of the proposal.
So far, our contract looks like this:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract ProposalContract {

    struct Proposal {
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

We have planned that our proposals will have ids to identify them in the mapping. For that we need some system so that we can track the ids of the proposals. So, what would that system be like?

The next part will be answering this question.


 This contract is a simple voting system for proposals created by the owner.  
 In proposals, we have a description for the explanation of the proposal. We also have variables for holding numbers of approve, reject and pass votes. We also have couple of additional fields that helps us to track more information about our proposals. 
 The owner can create a new proposal with a description and a vote limit, and other users can vote to approve, reject or pass the proposal.  
 The contract calculates the current state of the proposal based on the number of votes, and ends the proposal when the vote limit is reached.  
 The contract also keeps a history of all the proposals and their outcomes, and prevents users from voting more than once. 
 The contract uses some modifiers to restrict access and check conditions, and some helper functions to implement the logic.
