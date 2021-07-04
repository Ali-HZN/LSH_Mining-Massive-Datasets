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

<br>
<p align="center"><img src="https://github.com/Ali-HZN/LSH_Mining-Massive-Datasets/blob/main/images/shingles.JPG"/></p>