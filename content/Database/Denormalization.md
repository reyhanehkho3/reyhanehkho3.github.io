---
title: Denormalization
publish:
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** Denormalization is the intentional practice of **duplicating data or combining information from multiple tables** to make certain queries faster.  

It is usually done when joins become expensive or too frequent, trading **less efficient writes and more duplicate data** for faster reads. 

### Simple example

With **normalization**:

```text
Customers
id | name

Orders
id | customer_id | product
```

To display an order with the customer's name, you need a **JOIN**.

With **denormalization**:

```text
Orders
id | customer_id | customer_name | product
```

Now the customer's name is duplicated, but you can retrieve the order and name **without the JOIN**.

### 3 examples

1. **E-commerce:** Store `customer_name` directly inside `Orders` because order pages are viewed millions of times.
    
2. **Social media:** Store `post.comment_count` directly on a post instead of counting all comments every time someone opens the post.
    
3. **Analytics:** Store `product_name` and `category_name` directly in sales records so reports don't have to repeatedly join several large tables.
    

### Normalization vs. Denormalization

||Normalization|Denormalization|
|---|---|---|
|Duplicate data|Minimized|Intentionally introduced|
|Tables|More separated|May be combined|
|JOINs|More likely|Reduced|
|Reads|Can require more joins|Often faster|
|Writes|Easier to keep consistent|More places may need updating|
|Main goal|**Data consistency**|**Read performance**|

**Easy way to remember:**

> **Normalization:** “Don't repeat data; connect tables.”  
> **Denormalization:** “Repeat some data so I don't have to connect tables every time.” ([IBM](https://www.ibm.com/docs/en/db2/12.1.x?topic=glossary&utm_source=chatgpt.com "Glossary"))

And importantly, **denormalization doesn't mean bad database design**. You normally start with a well-normalized design and introduce denormalization when actual performance requirements justify the trade-off. ([Microsoft Learn](https://learn.microsoft.com/en-gb/ef/core/performance/modeling-for-performance?utm_source=chatgpt.com "Modeling for Performance - EF Core | Microsoft Learn"))


---
[[Database]]
[[My-Journey-In-Codeless]]