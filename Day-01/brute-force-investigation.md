# SOC Investigation Report — Day 1

Investigate a simulated brute-force attempt

Alert: Multiple failed logins followed by a successful login.
Time (UTC)	Username	Source IP	Result
09:00:01	analyst1	203.0.113.25	Failed
09:00:05	analyst1	203.0.113.25	Failed
09:00:09	analyst1	203.0.113.25	Failed
09:00:13	analyst1	203.0.113.25	Failed
09:00:18	analyst1	203.0.113.25	Success

**Incident:** Multiple failed logins followed by a successful login  
**Severity:** Pending triage; determine using organizational policy  
**Data source:** Fictional authentication log  
**Account:** analyst1  
**Source IP:** 203.0.113.25

## Observed evidence
- Four failed login attempts occurred between 09:00:01 and 09:00:13 UTC.
- A successful login was recorded at 09:00:18 UTC.
- All five events reference the same username and source IP.

## Initial assessment
The pattern is suspicious and may be consistent with password guessing followed by a successful authentication. The available evidence does not confirm account compromise.

## Recommended next steps
1. Review surrounding authentication events and any available MFA results.
2. Validate the source IP and login context using approved tools.
3. Check for unusual activity following the successful login.
4. Document findings and escalate according to SOC procedures.

## Conclusion
Further investigation is required before classifying this as a confirmed security incident.