# publish-node-package

GitHub action to publish a NodeJS package to NPM's package registry and GitHub
Packages.

## Usage

See [action.yml](action.yml). Make sure you've stored a NPM classic token (an
"Automation" token) as a secret in your repository. You can generate one at
[https://www.npmjs.com/settings/your-username/tokens](https://www.npmjs.com/settings/your-username/tokens).

## Example Workflow

```yaml
name: Publish My Node Package

on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest

    permissions:
      contents: read
      packages: write

    steps:
      - uses: actions/checkout@v3

      - uses: colinparsonsme/publish-node-package@v1
        with:
          # you can store your NPM token with any name in your repository secrets
          # assuming it's stored as NPM_TOKEN here
          npm_token: ${{ secrets.NPM_TOKEN }}
          # your github token is always accessed by ${{ secrets.GITHUB_TOKEN}}
          # since it's autogenerated by GitHub on each job
          github_token: ${{ secrets.GITHUB_TOKEN }}
          scope: @my-username-or-organization
```

## License

See the [License](LICENSE).

## Contributing

See the [Contributing Guidelines](CONTRIBUTING.md).

### Contributor Code of Conduct

See the [Code of Conduct](CODE-OF-CONDUCT.md).

## Contact

If you're interested in getting in touch outside of this project, check out
[colinparsons.com](https://colinparsons.com).
