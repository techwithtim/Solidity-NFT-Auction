# Solidity-NFT-Auction
A solidity smart contract for hosting an NFT auction.

## Disclaimer
Do NOT use this code in a production environment!

- withdraw() can be called before auction ends. Someone could bid and withdraw their bid in the same transaction and still be the highest bidder despite the contract having 0 eth in the contract

- seller can probably drain all of the bids once the auction is over using a re-entrancy attack when (bool sent, bytes memory data) = seller.call{value: highestBid}(""); is called. Seller contract's callback function just needs to call end() again to get paid a second time.

https://consensys.github.io/smart-contract-best-practices/known_attacks/
https://fravoll.github.io/solidity-patterns/checks_effects_interactions.html
