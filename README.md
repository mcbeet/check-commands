# Check minecraft commands

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
          source: foo.mcfunction
```

## Usage

This github action installs [`mecha`](https://github.com/mcbeet/mecha) in an isolated virtualenv and checks your data pack and function files for errors. The inputs of the action reflect the [`mecha` command-line options](https://github.com/mcbeet/mecha#command-line-utility). Only the `source` input is required.

| Input       | Optional              | Description                                                    |
| ----------- | --------------------- | -------------------------------------------------------------- |
| `version`   | defaults to `latest`  | The version of mecha to install                                |
| `source`    | required              | The list of data packs, functions files or folders to validate |
| `minecraft` | defaults to `1.17`    | The version of minecraft to use for checking commands          |
| `log`       | defaults to `WARNING` | The output log level                                           |

## Contributing

Contributions are welcome. Make sure to first open an issue discussing the problem or the new feature before creating a pull request. If you find a bug please try to share a link the problematic action run.

---

License - [MIT](https://github.com/mcbeet/check-commands/blob/main/LICENSE)
