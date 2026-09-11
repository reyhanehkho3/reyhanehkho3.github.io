---
title: YML
publish: true
date created: 2026-09-11
tags:
  - devops
---
**YML** usually means **YAML**, a human-readable format for writing **configuration and structured data**.

YAML files usually end with:

```text
.yml
```

or:

```text
.yaml
```

### Simple example

```yaml
name: my-app
version: 1.0
port: 3000
debug: true
```

This represents structured data:

```text
name    → my-app
version → 1.0
port    → 3000
debug   → true
```

### Why is YAML used?

It's very common for **configuration**, especially in development and DevOps.

For example, **GitHub Actions** uses YAML:

```yaml
name: Test

on:
  push:

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - run: npm install
      - run: npm test
```

This tells GitHub:

```text
When code is pushed
      ↓
start a Linux machine
      ↓
download the repository
      ↓
install dependencies
      ↓
run tests
```

### YAML vs JSON

Both can represent structured data.

JSON:

```json
{
  "name": "my-app",
  "port": 3000,
  "debug": true
}
```

YAML:

```yaml
name: my-app
port: 3000
debug: true
```

YAML is often easier for humans to read and write because it doesn't need `{}`, quotes, and commas everywhere.

### One important thing: indentation

YAML uses **indentation to represent structure**:

```yaml
server:
  host: localhost
  port: 3000
```

means:

```text
server
 ├── host: localhost
 └── port: 3000
```

So you need to be careful with spaces:

```yaml
server:
  host: localhost
```

is different from incorrectly structured indentation.

### Common places you'll see YAML

- GitHub Actions → `.github/workflows/test.yml`
    
- Docker Compose → `docker-compose.yml`
    
- Kubernetes → `.yaml` manifests
    
- CI/CD configuration
    
- Application configuration
    
- Infrastructure/DevOps tools
    

**Mental model:**

> **YAML = a human-friendly way to describe structured configuration/data.**


---
[[DevOps]]