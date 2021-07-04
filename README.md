# Locality-Sensitive Hashing (LSH)

### General Idea:
<div align="justify"><b>LSH</b> refers to a family of functions (known as LSH families) to hash data points into buckets so that data points near each other are located in the same buckets with high probability, while data points far from each other are likely to be in different buckets. This makes it easier to identify observations with various degrees of similarity.</div>

<br>
<p align="center"><img src="https://github.com/Ali-HZN/LSH_Mining-Massive-Datasets/blob/main/images/img_1.png"/></p>

<div align="justify">The problem we’re trying to solve is that <b> in a large collections of documents we want to find “near duplicate” pairs</b>. In the context of this problem, we can break down the LSH algorithm into 3  steps:<br></div>
<br>
- Shingling
- Min hashing
- Locality-sensitive hashing

<br>
<p align="center"><img src="https://github.com/Ali-HZN/LSH_Mining-Massive-Datasets/blob/main/images/img_2.png"/></p>

### Shingling:

<div align="justify">In this step, we convert each document into a set of characters of length k (also known as k-shingles or k-grams). The key idea is to represent each document in our collection as a set of k-shingles. For example One of the document (D): “Nadal”. Now if we’re interested in 2-shingles, then our set: {Na, ad, da, al}. Similarly set of 3-shingles: {Nad, ada, dal}. With this methodalogy Similar documents are more likely to share more shingles and reordering paragraphs in a document of changing words doesn’t have much affect on shingles. k value of 8–10 is generally used in practice. A small value will result in many shingles which are present in most of the documents (bad for differentiating documents).</div>

### Hashing:

<div align="justify">The idea of hashing is to convert each document to a small signature using a hashing function H. Suppose a document in our corpus is denoted by d. Then:</div>
<br>

- H(d) is the signature and it’s small enough to fit in memory
- If similarity(d1,d2) is high then Probability(H(d1)==H(d2)) is high
- If similarity(d1,d2) is low then Probability(H(d1)==H(d2)) is low
<br>
<div align="justify">Choice of hashing function is tightly linked to the similarity metric we’re using. For Jaccard similarity the appropriate hashing function is min-hashing.</div>

#### Min Hashing Algorithm:
<div align="justify">This is the critical and the most magical aspect of this algorithm so pay attention:</div>

- <b>Step 1</b>: Random permutation (π) of row index of document shingle matrix.
- <b>Step 2</b>: Hash function is the index of the first (in the permuted order) row in which column C has value 1. Do this several time (use different permutations) to create signature of a column.

<br>
<p align="center"><img src="https://github.com/Ali-HZN/LSH_Mining-Massive-Datasets/blob/main/images/minhash.JPG"/></p>

#### Min-hash property:

<div align="justify">The similarity of the signatures is the fraction of the min-hash functions (rows) in which they agree. So the similarity of signature for C1 and C3 is 2/3 as 1st and 3rd row are same. <b>Expected similarity of two signatures is equal to the Jaccard similarity of the columns. The longer the signatures, the lower the error</b>. In the below example you can see this to some extent.</div>

<br>
<p align="center"><img src="https://github.com/Ali-HZN/LSH_Mining-Massive-Datasets/blob/main/images/minhash2.JPG"/></p>

<div align="justify">So using min-hashing we have solved the problem of space complexity by eliminating the sparseness and at the same time preserving the similarity.</div>


