# Check minecraft commands

![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/mcbeet/check-commands)
[![Discord](https://img.shields.io/discord/900530660677156924?color=7289DA&label=discord&logo=discord&logoColor=fff)](https://discord.gg/98MdSGMm8j)

> Github action to validate minecraft data packs and function files.

```yml
# .github/workflows/check-commands.yml
name: Check commands
on: [push]

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: mcbeet/check-commands@v1
        with:
          source: path/to/my_data_pack
```

## Usage

This github action installs [`mecha`](https://github.com/mcbeet/mecha) in an isolated virtualenv and checks your data pack and function files for errors. The inputs of the action reflect the [`mecha` command-line options](https://github.com/mcbeet/mecha#command-line-utility). Only the `source` input is required.

| Input       | Optional              | Description                                                    |
| ----------- | --------------------- | -------------------------------------------------------------- |
| `version`   | defaults to `latest`  | The version of mecha to install                                |
| `source`    | required              | The list of data packs, functions files or folders to validate |
| `minecraft` | defaults to `1.19`    | The version of minecraft to use for checking commands          |
| `stats`     | defaults to `false`   | Whether to output statistics                                   |
| `log`       | defaults to `WARNING` | The output log level                                           |

## Examples

Check a data pack when the `pack.mcmeta` file is at the root of the repository.

```yml
- uses: mcbeet/check-commands@v1
  with:
    source: .
```

Check a data pack located in the `src` directory.

```yml
- uses: mcbeet/check-commands@v1
  with:
    source: src
```

Check individual function files.

```yml
- uses: mcbeet/check-commands@v1
  with:
    source: foo.mcfunction bar.mcfunction
```

Check a data pack at the root of the repository with an explicit minecraft version.

```yml
- uses: mcbeet/check-commands@v1
  with:
    source: .
    minecraft: "1.18"
```

Check a data pack at the root of the repository and output statistics.

```yml
- uses: mcbeet/check-commands@v1
  with:
    source: .
    stats: true
```

## Contributing

Contributions are welcome. Make sure to first open an issue discussing the problem or the new feature before creating a pull request. If you find a bug please try to share a link to the problematic action run.

---

License - [MIT](https://github.com/mcbeet/check-commands/blob/main/LICENSE)
