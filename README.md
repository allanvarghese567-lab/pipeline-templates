# pipeline-templates

Reusable secure GitHub Actions pipeline (`secure-pipeline.yml`).

## Tag the release

```bash
git tag v1
git push origin v1
```

Or create the tag on GitHub: Releases → Draft a new release → tag `v1`.

Callers should pin to `@v1` (or a full commit SHA for maximum security).

## Security model

- Workflow-level `permissions: {}` (deny by default)
- Jobs request least privilege
- Inputs are never interpolated directly into `run:` scripts (always via `env:`)
- Owner allow-list, branch safety checks, prod-only-from-main/release/*
- Cross-repo checkout uses a dedicated token with minimal scope
