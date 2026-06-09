Hashing – Division Method

1. Division Method of Hashing

The division method is one of the most common hash functions.

Formula:
h(k)= k mod m
Where:

k = key value
m = size of the hash table
h(k) = hash index (address)

2. Example

Let:

Hash table size m=10m = 10m=10

Keys = {2, 5, 16, 28, 139}

Hash values:

h(2) = 2 mod 10

h(5)=5 mod 10

h(16)=16 mod 10

h(28)=28 mod 10

h(139)=139 mod 10


3. Hash Table Representation

Index   0   1   2   3   4   5   6   7   8     9

Value   –   –   2   –   –   5  16   –   28    139




Add collision resolution techniques


Give MCQs + numericals based on this topic

