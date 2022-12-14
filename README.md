# valora-inc/renovate-config

Shareable [Renovate](https://renovatebot.com) config for Valora repositories.

## Usage

Add the following into your `renovate.json5`:

```json5
{
  extends: ['github>valora-inc/renovate-config:default.json5'],
}
```

## Presets

### default

Highlights:

- Automerges all updates during office hours (across PST and CET timezones), except on Fridays (no deploys on Fridays!!). This requires good test coverage and a good CI pipeline.
- Groups `devDependencies` with weekly automerges (reduces the noise since these tend to update frequently). With some exceptions to more clearly see updates (TypeScript, Prettier, etc).
- Dedupes lockfile entries

Please see [`default.json5`](default.json5) for more details.

## Useful Links

- [Configuration Options](https://docs.renovatebot.com/configuration-options/)
- [Renovate Presets](https://github.com/renovatebot/renovate/tree/main/lib/config/presets)
