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
has caused CI failures in cloud-functions and needed to be omitted. 

If the default config is not working well for a particular repo, and overriding some configs is not possible, 
then the base config can be used instead as follows:

```json5
{
  extends: ['github>valora-inc/renovate-config:base.json5'],
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
