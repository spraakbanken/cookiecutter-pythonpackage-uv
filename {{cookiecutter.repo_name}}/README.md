# {{ cookiecutter.project_name }}

[![PyPI version](https://img.shields.io/pypi/v/{{ cookiecutter.project_name }}.svg)](https://pypi.org/project/{{ cookiecutter.project_name }}/)
[![PyPI license](https://img.shields.io/pypi/l/{{ cookiecutter.project_name }}.svg)](https://pypi.org/project/{{ cookiecutter.project_name }}/)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/{{ cookiecutter.project_name }}.svg)](https://pypi.org/project/{{ cookiecutter.project_name }})

[![Maturity badge - level 1](https://img.shields.io/badge/Maturity-Level%201%20--%20New%20Project-yellow.svg)](https://github.com/spraakbanken/getting-started/blob/main/scorecard.md)
[![Stage](https://img.shields.io/pypi/status/{{ cookiecutter.project_name }}.svg)](https://pypi.org/project/{{ cookiecutter.project_name }}/)

[![codecov](https://codecov.io/gh/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/graph/badge.svg?token=DUV4CL6AK2)](https://codecov.io/gh/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }})

[![CI(check)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/check.yml/badge.svg)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/check.yml)
[![CI(release)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/release.yml/badge.svg)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/release.yml)
[![CI(scheduled)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/rolling.yml/badge.svg)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/rolling.yml)
[![CI(test)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/test.yml/badge.svg)](https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}/actions/workflows/test.yml)

{{ cookiecutter.description }}

## Minimum Supported Python Version Policy

The Minimum Supported Python Version is fixed for a given minor (1.x)
version. However it can be increased when bumping minor versions, i.e. going
from 1.0 to 1.1 allows us to increase the Minimum Supported Python Version. Users unable to increase their
Python version can use an older minor version instead. Below is a list of {{ cookiecutter.project_name }} versions
and their Minimum Supported Python Version:

- v{{ '.'.join(cookiecutter.version.split('.')[:2]) }}: Python {{ cookiecutter.min_python_version }}.

Note however that sparv-sbx-corpus-statistics also has dependencies, which might have different MSRV
policies. We try to stick to the above policy when updating dependencies, but
this is not always possible.

## Changelog

This project keeps a [changelog](./CHANGELOG.md).

## License

This repository is licensed under the [MIT](./LICENSE) license.

## Development

### Development prerequisites

- [`uv`](https://docs.astral.sh/uv/)
- [`prek`](https://prek.j178.dev/) (or [`pre-commit`](https://pre-commit.org))

For starting to develop on this repository:

- Clone the repo (in one of the ways below):
  - `git clone git@github.com:{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}.git`
  - `git clone https://github.com/{{ cookiecutter.github_handle }}/{{ cookiecutter.repo_name }}.git`
- Setup environment: `make dev`
- Install `pre-commit` hooks: `prek install` (or `pre-commit install`)

Do your work.

Tasks to do:

- Test the code with `make test` or `make test-w-coverage`.
- Lint the code with `make lint`.
- Check formatting with `make check-fmt`.
- Format the code with `make fmt`.
- Type-check the code with `make type-check`.

This repo uses [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/).

### Release a new version

> [!NOTE] Requirements
> [`bump-my-version`](https://github.com/callowayproject/bump-my-version) for `make bumpversion`, install with `uv tool install bump-my-version`.
> [`git-cliff`](https://git-cliff.org/) for `make prepare-release`

- Prepare the CHANGELOG: `make prepare-release`.
- Edit `CHANGELOG.md` to your liking. Keep the header `[unreleased]`
- Add to git: `git add --update`
- Commit with `git commit -m 'chore(release): prepare release'` or `cog commit chore 'prepare release' release`.
- Bump version (depends on [`bump-my-version](https://callowayproject.github.io/bump-my-version/))
  - Major: `make bumpversion part=major`
  - Minor: `make bumpversion part=minor`
  - Patch: `make bumpversion part=patch` or `make bumpversion`
- Push `main` and tags to GitHub: `git push main --tags` or `make publish`
  - [GitHub Actions workflow](./.github/workflows/release.yaml) will build, test and publish the package to [PyPi](https://pypi.prg).
