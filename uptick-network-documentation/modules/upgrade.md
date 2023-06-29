---
description: This module provides the basic functions of software version upgrade.
---

# Upgrade

### Available Commands

<table><thead><tr><th width="269">Name</th><th>Description</th></tr></thead><tbody><tr><td>software-upgrade</td><td>Submit a software upgrade proposal</td></tr><tr><td>cancel-software-upgrade</td><td>Cancel the current upgrade proposal</td></tr><tr><td>plan</td><td>Query the software upgrade plan currently in progress</td></tr><tr><td>applied</td><td>Query the executed software upgrade plan</td></tr></tbody></table>

#### uptickd query upgrade plan

Query the currently ongoing software upgrade plan.

```Bash
uptickd query upgrade plan [flags]
```

### uptickd query upgrade applied

Query the software upgrade plan that has been executed recently.

```Bash
  uptickd query upgrade applied [upgrade-name] [flags]
```
