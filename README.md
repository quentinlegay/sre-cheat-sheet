# SRE Cheat Sheet

## Principles
1. Reliability is the most important feature
2. Users, not monitoring decide reliability
3. Well-engineered (can go only to 3 9s)
 - software = 99.9%
 - operations = 99.99%
 - business = 99.999%
 
Note: Taking reliaility to extreme measures is unproductiove and costly. It should be "Reliable Enough"

### Error budget
Error budgets are the tool SRE uses to balance service reliability with the pace of innovation. Changes are a major source of instability, 
representing roughly 70% of our outages, and development work for features competes with development work for stability. 
The error budget forms a control mechanism for diverting attention to stability as needed.

An error budget is 1 minus the SLO of the service. A 99.9% SLO service has a 0.1% error budget.

If our service receives 1,000,000 requests in four weeks, a 99.9% availability SLO gives us a budget of 1,000 errors over that period.

### Example
---
28 day error budget
- 99.9% = 40 min (Enough time for humans to react)
- 99.99% = 4 minutes 
(Incident responses have to be automated. 
Else make sure change propagates gradually so not all parts of system 
are exposed to change at once giving time for human intervention)
- 99.999% = 24 seconds (Restricting the rate of change so that only 1% of system changes at a given point in time)

### SLI
An SLI is a service level indicator—a carefully defined quantitative measure of some aspect of the level of service that is provided.
- Request Latency
- Error Rate = (500 responses/total requestes) per second
- Availability = uptime / (uptime + downtime)
- Durability (Data will be retained over a period of time, measure of data loss)

---
Examples

- User-facing serving systems - availability, latency, and throughput.

- Storage systems - latency, availability, and durability

- Big data systems - throughput and end-to-end latency

```
Although 100% availability is impossible, near-100% availability is often readily achievable, 
and the industry commonly expresses high-availability values in terms of the number of "nines" 
in the availability percentage. 
For example, 
availabilities of 99% and 99.999% can be referred to as "2 nines" and "5 nines" availability, respectively, 
and the current published target for Google Compute Engine availability is “three and a half nines”—99.95% availability.
```

### SLO
An SLO is a service level objective: a target value or range of values for a service level that is measured by an SLI.
They are a fundamental tool in helping your organization strike a good balance between releasing new features and staying reliable for your users. 
They also help your teams communicate on the expectations of a service through objective data.
Questions that SLO help answer:
- If reliability is a feature, when do you prioritize it versus other features?
- How fast is too tast for rolling out features?
- What is the right level of reliability for your system?
  Desired Reliability principles
  - What to promise and to whom?
  - What metrics to measure?
  - How much reliability is good enough?
  
```
lower bound ≤ SLI ≤ upper bound
```
