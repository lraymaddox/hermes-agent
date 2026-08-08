# Releasing hermes-agent

## Branch model (Option A — adopted 2026-08-08)

```
   feature/*  --push-->  develop  --merge-->  main
                           |                     |
                           v                     v
                   testing candidate     release binary
```

| Branch | Role |
|---|---|
| `main` | Current release |
| `develop` | Next release candidate |
| `feature/*` | Individual changes |

## Workflow

1. Develop on `feature/*` branches from `develop`
2. Test by merging to `develop`
3. Release when ready: `git checkout main && git merge --ff-only origin/develop && git push`
4. Advance develop: `git checkout develop && git merge --ff-only main && git push`

## Hard rules

- **Never force-push `main`**
- **Never force-push `develop` without user confirmation**
- **Always `--ff-only`** when promoting develop → main
- **4-ref verify** after every push: main / origin/main / develop / origin/develop
