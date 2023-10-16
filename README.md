# valora-inc/renovate-config

Shareable [Renovate](https://renovatebot.com) config for Valora repositories.

## Usage

### Default

Add the following into your `renovate.json5`:

```json5
{
  extends: ['github>valora-inc/renovate-config:default.json5'],
}
```

### Base

The "base" renovate config is a subset of the default config that is intended for repositories where the default options are
causing problems that cannot be solved with a simple override. An example of this is `postUpdateOptions`, which
[cannot be overridden](https://github.com/renovatebot/renovate/discussions/25112#discussioncomment-7239388) (just 
extended), and needed to be omitted in cloud-functions to prevent CI failures.

If the Valora default presets are not working well for a particular repo, and overriding some offending config(s) is 
not possible, then the Valora base presets can be used instead as follows:

```json5
{
  extends: ['github>valora-inc/renovate-config:base.json5'],
}
```

## Overrides

In general, configs can be overridden for some repo even if they are defined in the presets file. Some configs are marked
as ["mergeable"](https://docs.renovatebot.com/configuration-options/) in the Renovate docs, which means they can be 
extended, but not necessarily overridden.

Examples:
- overriding non-mergeable config where preset sets `semanticCommits` to 'enabled':
```json5
{
  extends: ['github>valora-inc/renovate-config:default.json5'],
  semanticCommits: 'disabled'
}
```
- overriding mergeable config where preset disables updates for peer dependencies and engines:
```json5
{
  extends: ['github>valora-inc/renovate-config:default.json5'],
  packageRules: [{
    matchDepTypes: ['peerDependencies', 'engines'],
    enabled: true,
  }]
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
