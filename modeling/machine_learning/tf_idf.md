# TF-IDF

**Term Frequency - Inverse Document Frequency**

t: Term

d: Document

**TF**: Indicates how often a term appears in a document

$$
TF(t,d) = \frac{freq \ of \ t^{th} \ term \ in \ d^{th} \ doc}{\# \ terms \ in \ document \ d}
$$

**IDF**: measures the importance of a term across a collection of documents

$$
IDF(t)=log(\frac{\# \ of \ docs}{\# \ of \ docs \ containing \ term \ t})
$$

$$
TF-IDF = IF(t,d) \times IDF(t)
$$