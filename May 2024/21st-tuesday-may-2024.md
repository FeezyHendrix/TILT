For Blockchains when the latest transaction in a coin in buried under enough blocks, past transactions can be discarded to save disk space. 

To facilitate this which old transaction are hashed in a Merkle Tree. 

```
package main

import (
	"crypto/sha256"
	"encoding/hex"
	"fmt"
)

type MerkleTree struct {
	Root       *Node
	LeafHashes [][]byte
}

type Node struct {
	Left  *Node
	Right *Node
	Hash  []byte
}


func hashData(data []byte) []byte {
	hash := sha256.Sum256(data)
	return hash[:]
}

func concatenateAndHash(left, right []byte) []byte {
	concatenated := append(left, right...)
	return hashData(concatenated)
}

func NewMerkleTree(data [][]byte) *MerkleTree {
	var nodes []Node

	// Create leaf nodes
	for _, datum := range data {
		hash := hashData(datum)
		nodes = append(nodes, Node{Hash: hash})
	}

	// Build the tree
	for len(nodes) > 1 {
		var newLevel []Node
		for i := 0; i < len(nodes); i += 2 {
			if i+1 == len(nodes) {
				// Odd number of nodes, duplicate the last node
				nodes = append(nodes, nodes[i])
			}
			left, right := nodes[i], nodes[i+1]
			newHash := concatenateAndHash(left.Hash, right.Hash)
			newLevel = append(newLevel, Node{Left: &left, Right: &right, Hash: newHash})
		}
		nodes = newLevel
	}

	tree := MerkleTree{Root: &nodes[0]}
	return &tree
}


func printTree(node *Node, level int) {
	if node == nil {
		return
	}
	fmt.Printf("%*s%s\n", level*2, "", hex.EncodeToString(node.Hash))
	printTree(node.Left, level+1)
	printTree(node.Right, level+1)
}


func main() {
	data := [][]byte{
		[]byte("data1"),
		[]byte("data2"),
		[]byte("data3"),
		[]byte("data4"),
	}

	tree := NewMerkleTree(data)
	printTree(tree.Root, 0)
}



```


It is possible to verify payments without running the full network node. 

Following the prediction from the bitcoin book of 1.2GB per year we now have over 420GB of bitcoin mined.

Verifying payments on a blockchain network is possible without running the full network node. We need a copy of the block headers of the longest proof-of-work chain. Which he can get by querying the network nodes until he is convinced he has the longest chain, then obtaining the Merkle branch linking the transaction to the block it's timestamped in.  The only way to verify if the transaction has been accepted is by linking it to place in the chain and see if other blocks are added after it to confirm that the network has accepted it.



> [!NOTE] Question: What happens when the node the user is convinced is the longest chain but isn't?
> The Query of nodes gathers multiple block headers, By doing this the node collects information about the chains that different nodes have. It compares the chains by their cumulative proof-of-work which is the difficulty of the blocks. The chain with the greatest cumulative difficulty is the considered to be the longest chain.

 A binomial random walk is a mathematical model which consist of a series of random steps. The model is often used to represent various types of stochastic processes.  A step is a binomial process which has two outcome up or down movement. 

In blockchain the race between an honest chain and an attacker to be the longest chain is a binomial random walk, where the success event is the honest chain extended by one block +1 and the failure event is the attacker's chain extending by one block reducing the gap by -1 .



https://astexplorer.net/ cool site to check the AST compilation of your code. 