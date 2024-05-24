 Micro plastics are small debris less than 5mm long which are harmful.

Merkle trees are checksums to check if you have the correct data by comparing the hash of the validate data to the data you have. 

Macros allow you to encapsulate sequence of instructions to execute, as a code that write itself, macros allow to abstract repetitive operations. 

An example of a Macro would be a json! macro

```
#[macro_use]
extern crate serde_json;

macro_rules! json {
    // Match for null
    (null) => {
        serde_json::Value::Null
    };
    // Match for boolean
    (true) => {
        serde_json::Value::Bool(true)
    };
    (false) => {
        serde_json::Value::Bool(false)
    };
    // Match for number
    ( $e:expr ) => {
        serde_json::Value::Number(serde_json::Number::from($e))
    };
    // Match for string
    ( $e:expr ) => {
        serde_json::Value::String($e.to_string())
    };
    // Match for an array
    ( [ $( $e:tt ),* ] ) => {
        serde_json::Value::Array(vec![ $( json!($e) ),* ])
    };
    // Match for an object
    ( { $( $key:tt : $value:tt ),* } ) => {
        {
            let mut object = serde_json::Map::new();
            $(
                object.insert($key.to_string(), json!($value));
            )*
            serde_json::Value::Object(object)
        }
    };
}

fn main() {
    // Create a JSON object using the custom json macro
    let data = json!({
        "name": "John Doe",
        "age": 30,
        "is_admin": false,
        "address": {
            "street": "123 Main St",
            "city": "Anytown"
        },
        "phones": ["123-456-7890", "987-654-3210"]
    });

    // Print the JSON object
    println!("{}", data.to_string());
}

```

An example of a macro rule for a Merkle Tree

```
use sha2::{Sha256, Digest};
use std::fmt;

#[derive(Debug, Clone)]
struct MerkleNode {
    Leaf { hash: Vec<u8> },
    Node { left: Box<MerkleNode>, right: Box<MerkleNode>, hash: Vec<u8> },
}

impl fmt::Display for MerkleNode {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        match self {
            MerkleNode::Leaf { hash } => write!(f, "Leaf({:x?})", hash),
            MerkleNode::Node { hash, .. } => write!(f, "Node({:x?})", hash),
        }
    }
}

impl MerkleNode {
    fn hash(data: &[u8]) -> Vec<u8> {
        let mut hasher = Sha256::new();
        hasher.update(data);
        hasher.finalize().to_vec()
    }

    fn combine_hashes(left: &[u8], right: &[u8]) -> Vec<u8> {
        let mut hasher = Sha256::new();
        hasher.update(left);
        hasher.update(right);
        hasher.finalize().to_vec()
    }

    fn new_leaf(data: &[u8]) -> MerkleNode {
        MerkleNode::Leaf { hash: MerkleNode::hash(data) }
    }

    fn new_node(left: MerkleNode, right: MerkleNode) -> MerkleNode {
        let hash = MerkleNode::combine_hashes(&left.hash(), &right.hash());
        MerkleNode::Node { left: Box::new(left), right: Box::new(right), hash }
    }

    fn hash(&self) -> &[u8] {
        match self {
            MerkleNode::Leaf { hash } => hash,
            MerkleNode::Node { hash, .. } => hash,
        }
    }
}

macro_rules! merkle_tree {
    ( $($data:expr),* ) => {
        {
            // Collect the data into a vector
            let data_vec = vec![$($data),*];

            // Create the leaf nodes
            let mut nodes: Vec<MerkleNode> = data_vec
                .iter()
                .map(|data| MerkleNode::new_leaf(data.as_bytes()))
                .collect();

            // Build the tree by combining nodes until one root node is left
            while nodes.len() > 1 {
                let mut next_level = Vec::new();

                for chunk in nodes.chunks(2) {
                    let node = if chunk.len() == 2 {
                        MerkleNode::new_node(chunk[0].clone(), chunk[1].clone())
                    } else {
                        chunk[0].clone()  // If odd number of nodes, carry the last one to the next level
                    };

                    next_level.push(node);
                }

                nodes = next_level;
            }

            nodes.pop().unwrap()  // The root node
        }
    };
}

```