`pnpm install --frozen-lockfile` does not throw an error when the lockfile is out of sync with the package.json

## pnpm-workspace.yaml

- refer `lodash@4.0.0` in the workspace file

```json5
catalog:
  lodash: 4.0.0
```

## pnpm-lock.yaml

- refer `lodash@4.17.21` in the lockfile

```yaml
lockfileVersion: '9.0'

settings:
  autoInstallPeers: true
  excludeLinksFromLockfile: false

catalogs:
  default:
    lodash:
      specifier: 4.17.21
      version: 4.17.21

importers:

  .:
    dependencies:
      lodash:
        specifier: 'catalog:'
        version: 4.17.21

packages:

  lodash@4.17.21:
    resolution: {integrity: sha512-v2kDEe57lecTulaDIuNTPy3Ry4gLGJ6Z1O3vE1krgXZNrsQ+LFTGHVxVjcXPs17LhbZVGedAJv8XZ1tvj5FvSg==}

snapshots:

  lodash@4.17.21: {}

```


## Reproduce Steps

1. Run `pnpm install --frozen-lockfile` in the workspace root directory

```
pnpm install --frozen-lockfile
```

However, the command does not throw an error in pnppnpm@10.7.1.

## Expected Behavior

- The command should throw an error indicating that the lockfile is out of sync with the package.json.

## Actual Behavior

- The command does not throw an error, and the lockfile is not updated to match the package.json.

