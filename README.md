# linux-permission-inspector

Decode Unix permission bits and flag world-writable files.

## Run

Python 3.8 or later; no third-party packages or cloud credentials are required.

```sh
python3 tool.py examples/input.json
cat examples/input.json | python3 tool.py -
python3 -m unittest -v
```

## Example

Input:

```json
{
  "mode": "0750"
}
```

Result:

```json
{
  "owner": 7,
  "group": 5,
  "other": 0,
  "world_writable": false,
  "setuid": false,
  "sticky": false
}
```

The command writes JSON to standard output. Exit 0 means evaluation completed;
a finding in the output may still require attention. Invalid input returns exit 2,
with an error on standard error and no result on standard output.

## Operational scope

Decodes supplied metadata; does not inspect ACLs, ownership, or effective permissions.

The tool evaluates supplied data locally. It does not change hosts, deploy
resources, or establish production compliance. Example identifiers and observations
are test fixtures. Keep credentials and private inventory out of Git.

## Design and verification

See [NOTES.md](NOTES.md) for the input contract, verification, and integration notes.
Related utilities: [uid-collision-detector](https://github.com/sal-s-root/uid-collision-detector), [service-port-inventory](https://github.com/sal-s-root/service-port-inventory).

## Project status

A small standalone learning exercise using supplied fixtures. The related
[infrastructure toolbox](https://github.com/sal-s-root/infra-toolbox) collects these
checks in one place.

The assigned historical dates form a retrospective learning schedule; this
exercise was created or reconstructed in 2026. See [history and scope](HISTORY.md).
