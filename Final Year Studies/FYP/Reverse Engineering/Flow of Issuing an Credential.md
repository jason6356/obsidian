
## Prerequisites

The Issuer should have their DID seeds registered into the von-network

The issuer should created their own Schema and Definition

## The states of each credentials

There are multiple states based on the reverse engineering studied from the previous batch work

Here are the states for each of the credential request

1. Holder creates a credential request to issuer (Proposal Sent)
2. Issuer receives the credential request from the holder (Proposal Received)
3. Issuer approves the proposal (Proposal Received)
4. Holder receives the offer from the Issuer (Offer Received)
5. Holder sends the credential request to the Issuer (Request-Sent)
6. Issuer receives the request and send the credential to holder (Request Received)
7. Holder receives the credential and store into the wallet (Credential-Received)