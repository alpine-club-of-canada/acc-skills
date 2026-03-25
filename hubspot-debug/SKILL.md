---
name: hubspot-debug
description: Debug HubSpot workflow issues, membership sync problems, and coded action errors for ACC
---

# Debug HubSpot Issues

## Instructions

When debugging HubSpot workflow or sync issues for ACC:

### Environment
- Always use `process.env.HUBSPOT_API_TOKEN` — never `HUBSPOT_ACCESS_TOKEN` or other variants.

### Debugging Steps

1. **Check workflow execution history first.** Open the workflow in HubSpot and review recent execution logs before making assumptions about what's broken.

2. **Verify subscription-contact associations.** Many sync issues stem from contacts not being properly associated with their subscription (membership) records. Confirm the association exists and the association label is correct.

3. **Check for race conditions in membership sync.** HubSpot workflows can fire concurrently. If a workflow updates a contact property that another workflow depends on, the order of execution matters. Look for:
   - Multiple workflows triggered by the same event
   - Workflows with delays that may overlap with other workflow executions
   - Property values that seem stale or inconsistent

4. **Review coded action logs.** In the workflow execution history, expand coded action steps to see console.log output and error messages. Check for:
   - API rate limit errors (429 responses)
   - Missing or expired API tokens
   - Unexpected null values from API responses
   - Timeout errors (coded actions have a 20-second limit)

5. **Check CData Connect** if the issue involves QuickBooks data. Verify the connection is active and the query returns expected results.
