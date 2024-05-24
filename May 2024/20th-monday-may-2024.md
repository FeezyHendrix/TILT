
Bitcoin Transactions are essentially hashed items in block that are timestamped that proves that the data must have existed in a particular time. 

Similar to a linked list each timestamp has a link to the previous timestamp and the next timestamp

---<hash 2/10/22> <----->  hash 2/10/22> ----->  hash 2/10/24>.


The proof of work system works similarly in a way to consensus system where the network node with the longest chain is the source of truth, such that the candidate with the highest vote is regarded as the president to lead the country. Thus one CPU is regarded as a vote. 

An attacker might want to gather all of the most cpus in the world and want to be the longest chain, but the attacker would have to redo the proof of work of all the past blocks to catch up to the current block which might even have new blocks as the blockchain is receiving new transactions.

Blockchain nodes with always consider the longest chain as the correct one and will only work on extending it. If two nodes broadcast different version of the next block simultaneously,  Some node might receive different version of the nodes at different times, firstly they would work on the first block they received first, and save the other in case that block ends up extending into the longer chain where they discard the current one when the next proof-of-work is found and one branch becomes longer. Then the other nodes switch to the longer one.

First transaction in a block is known as the Genesis Block. This signifies the start of a new coin owned by the creator of the block. Like gold mining, coin mining is similar unlike machines and shovels, we have CPU time and electricity to the work, thus while expending this resources to mint out new coins in circulation an incentive called Transaction fees are given to miners. 

"If the output value of a transaction is less than the it's input value, the difference is a transaction fee that is added to the incentive value of the block containing the transaction". 

The incentive help encourage attacker to stay honest as playing by the rules is much more profitable than stealing all payments or generating new coins. 


