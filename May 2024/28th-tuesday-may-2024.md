```
class HashTable:
    def __init__(self):
        self.table = [[] for _ in range(10)] 

    def hash_function(self, key):
        return len(key)

    def insert(self, country, capital):
        index = self.hash_function(country)
        for pair in self.table[index]:
            if pair[0] == country:
                pair[1] = capital  # Update existing entry
                return
        self.table[index].append((country, capital))  # Insert new entry

    def get(self, country):
        index = self.hash_function(country)
        for pair in self.table[index]:
            if pair[0] == country:
                return pair[1]
        return None

# Create a hash table
hash_table = HashTable()

# Insert "Spain, Madrid"
hash_table.insert("Spain", "Madrid")

# Insert "India, Delhi"
hash_table.insert("India", "Delhi")

# Retrieve capitals
print(hash_table.get("Spain"))  # Output: Madrid
print(hash_table.get("India"))  # Output: Delhi

```

Hash Tables
A **hash table** (or hash map) is a data structure that provides a highly efficient way to store and retrieve data based on keys. It uses a technique called **hashing** to convert keys into array indices (hash codes), allowing for quick data access.

A collision occurs in a hash table, when two different keys have been hashed to the same index in the array that backs the hash table. 

From the example above our hash table, hashes the index based of the length of the key provided. thus a collision occurs where `spain` is being replaced by `india`

**Doorway Effect**
Apparently this is term of what happens when you forget what you went in a room to do. It is a psychological phenomenon characterised by short-term memory. 


**Changing the Name Server in a DNS entry change can take from 1 hour to 24 hour, why does this happen?**

This happens because of "DNS propagation" this is due to the nature of how DNS information is cached and distributed across the internet. Each DNS resolver caches the records based on TTL values, these caches need to expire to be refreshed. It generally takes about 24 hours for changes to fully propagate worldwide.


**Angular pipes** are pure by default.  Thus they only recalculate the value when the input changes like a pure function. 

An Impure Angular Pipe is one that changes on every change detection cycle regardless if the inputs have changed or not. 

To create an impure pipe, you need to set the `pure` property to `false` in the pipe's metadata:

```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'impureExample',
  pure: false
})
export class ImpureExamplePipe implements PipeTransform {
  transform(value: any, ...args: any[]): any {
    // Your transformation logic here
    return transformedValue;
  }
}

```

ngOnChanges lifecycle hook is a lifecycle that angular calls whenever one or more data-bound input properties change. 


Pizza Hut, made the very first online sale in the world in 1994 with Pizza net, and they couldn't pay online, they had to pay when delivery show up with their pizza. 


---


The Internet: Layers of open protocol

Ethernet - 1974

TCP/IP - 1974

Http - 1990

SSL / TLS - 1996



Cryptography is communication in the presence of adversaries. 

SSL mounts on top TPC stack to provide a layer of security. 

SSL is asymmetric cryptography.

Mpesa  figured out how to help kenyas that trade mobile minutes to efficiently do it. 

Satoshi Nakamoto solved the issue we had of trying to not have a central figure when doing online payment transactions. 


So what is a blockchain?

So they are timestamped append logs, satoshi didn't invent blockchain.  Stuart Haber and Stornetta did.

The longest running blockchain has been running since 1995.

Consensus on who gets to append the next block is an important thing in blockchain.

Blockchain move verifiable data across the network. The data can be value like bitcoin or like code in terms of smart contracts. 

Role of Money?

- Medium of exchange 
- Store of value
- Unit of Account

Role of Finance?

-  Moving, Allocation and Pricing. 
- Movement of Risk throughout of the economy. 

