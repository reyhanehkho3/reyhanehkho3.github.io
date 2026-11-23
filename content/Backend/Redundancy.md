---
title: Redundancy
publish:
date created: 2026-11-16
tags:
  - backend
---
**Redundancy** means having extra or duplicate components in a system so that if one fails, another can take its place.

The main goal is to **improve reliability and prevent system failures**.

## **1. Redundancy in Engineering**

Adding backup components to prevent a system from failing.

**Example: Airplanes**

- An airplane has two engines.
    
- If one engine fails, the other can keep the airplane flying.
    
- The second engine provides redundancy.
    

## **2. Redundancy in Computer Science**

Having duplicate hardware, data, or systems to keep a computer system running if something fails.

### **Types of Redundancy**

- **Hardware Redundancy:** Having extra hardware components, such as backup power supplies or servers.
    
- **Data Redundancy:** Storing multiple copies of data, such as RAID 1 disk mirroring.
    
- **Network Redundancy:** Having multiple network connections or routers.
    
- **Software Redundancy:** Running multiple instances of an application so another can take over if one crashes.
    

## **3. Related Concepts**

|Term|Meaning|
|---|---|
|Redundancy|Having extra or duplicate resources|
|Single Point of Failure (SPOF)|One component whose failure can bring down the entire system|
|Fault Tolerance|Ability to continue operating despite failures|
|High Availability (HA)|Designing systems to minimize downtime|

## **4. Example: Database Redundancy**

Imagine having two PostgreSQL servers:

- **Primary:** Handles database operations.
    
- **Standby:** Receives replicated data and acts as a backup.
    

If the primary server fails, the standby can take over.

## **5. Is Redundancy Always Good?**

No. Redundancy can introduce:

- Higher infrastructure costs.
    
- More maintenance.
    
- Greater system complexity.
    
- Data synchronization problems.
    

**In short:** Redundancy means having backups or duplicates so that one component's failure doesn't cause the entire system to stop working.


---
[[Backend]]