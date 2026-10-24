
## Practical Commands and Results

The following commands were used to investigate the synthetic authentication log:

```bash
grep -ic "failed password" auth.log
grep -ic "Failed password for alice" auth.log
grep -i "Accepted" auth.log
```

### Observed Results

- Total failed authentication records: 6
- Failed authentication records for Alice: 5
- Successful authentication records: 2
- Repeated failures from one source IP: 5

### Investigation Methodology

1. Searched the authentication log for failed login events.
2. Counted the failed authentication records.
3. Identified the account associated with repeated failures.
4. Extracted and counted source IP addresses.
5. Reviewed successful authentication events.
6. Documented the initial assessment and recommended follow-up checks.

### Skills Demonstrated

- Linux command-line fundamentals
- Log filtering and text processing
- Basic authentication-event analysis
- Evidence-based security investigation
- Technical documentation

### Verification Status

This exercise used synthetic data. The results demonstrate basic log-analysis practice, not experience investigating a production security incident.
