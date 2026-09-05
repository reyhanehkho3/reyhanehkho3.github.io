---
title: Business Transaction
publish: true
date created: 2026-09-05
tags:
  - database
  - codeless
---
**Definition:** A business transaction is a **real-world business action or process** that accomplishes a specific business goal, often involving an exchange of money, products, information, or services. ([ScienceDirect](https://www.sciencedirect.com/topics/computer-science/business-transaction?utm_source=chatgpt.com "Business Transaction - an overview | ScienceDirect Topics"))  
In software, one business transaction can involve **multiple operations or systems** that together complete that business action—for example, buying a product. ([IBM](https://www.ibm.com/docs/en/integration-bus/10.0.0?topic=interface-creating-business-transaction-definition&utm_source=chatgpt.com "Creating a business transaction definition"))

### 3 examples

1. **Buying a product**
    
    ```text
    Place order
       ↓
    Check inventory
       ↓
    Take payment
       ↓
    Create order
       ↓
    Send confirmation
    ```
    
    All of this together represents the **business transaction: “Purchase Product.”**
    
2. **Booking a flight**
    
    ```text
    Select flight
       ↓
    Reserve seat
       ↓
    Process payment
       ↓
    Issue ticket
    ```
    
    The business goal is **“Book a flight.”**
    
3. **Bank transfer**
    
    ```text
    Account A: -$100
    Account B: +$100
    ```
    
    Both changes belong to the business action **“Transfer $100 from A to B.”** If you're talking specifically about the **database transaction**, the two changes should be handled as one atomic unit so they don't partially succeed. ([Microsoft Learn](https://learn.microsoft.com/en-us/windows/win32/ktm/what-is-a-transaction?utm_source=chatgpt.com "What is a Transaction? - Win32 apps | Microsoft Learn"))
    

### Business transaction vs. database transaction

This distinction is **very important**:

> **Business transaction = what the business wants to accomplish.**  
> **Database transaction = how database operations are grouped to safely make changes.**

For example, **“Buy a laptop”** is a business transaction, while the database might use several transactions/operations to update the order, inventory, payment record, etc. A business transaction can therefore be **larger than a single database transaction**, especially when multiple services or systems are involved. ([ScienceDirect](https://www.sciencedirect.com/topics/computer-science/business-transaction?utm_source=chatgpt.com "Business Transaction - an overview | ScienceDirect Topics"))