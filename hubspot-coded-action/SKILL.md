---
name: hubspot-coded-action
description: Scaffold or review HubSpot coded actions following ACC conventions
---

# HubSpot Coded Actions — ACC Conventions

## Instructions

When scaffolding or reviewing HubSpot coded actions:

### Function Signature

Every coded action must export an async `main` function:

```javascript
exports.main = async (event, callback) => {
  // event.inputFields contains workflow property values
  // callback({ outputFields: { ... } }) to return data to the workflow
};
```

### Environment Variable

Always use `process.env.HUBSPOT_API_TOKEN` for API authentication. Never use `HUBSPOT_ACCESS_TOKEN` or hardcode tokens.

### Error Handling

Wrap the entire body in try/catch and always call the callback, even on failure:

```javascript
exports.main = async (event, callback) => {
  try {
    const token = process.env.HUBSPOT_API_TOKEN;
    // ... your logic ...
    callback({ outputFields: { result: "success" } });
  } catch (err) {
    console.error("Coded action failed:", err.message);
    callback({ outputFields: { result: "error", errorMessage: err.message } });
  }
};
```

### Async/Await

- Use `async/await` for all API calls — avoid raw Promise chains.
- Use `axios` (available by default in HubSpot coded actions) for HTTP requests.
- Remember the 20-second execution timeout. For batch operations, process in small chunks.

### Input/Output Fields

- Declare input fields in the workflow UI before referencing them in `event.inputFields`.
- Return meaningful output fields so downstream workflow actions can branch on success/failure.
- Use `console.log()` for debugging — output appears in workflow execution history.
