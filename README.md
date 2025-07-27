# MegaLinter Custom Flavor

npm-groovy-lint

## Embedded linters

  - DOCKERFILE_HADOLINT
  - GROOVY_NPM_GROOVY_LINT
  - JAVASCRIPT_PRETTIER
  - JSON_JSONLINT
  - JSON_NPM_PACKAGE_JSON_LINT
  - JSON_PRETTIER
  - JSON_V8R
  - MARKDOWN_MARKDOWNLINT
  - MARKDOWN_MARKDOWN_TABLE_FORMATTER
  - REPOSITORY_CHECKOV
  - REPOSITORY_GITLEAKS
  - REPOSITORY_GIT_DIFF
  - REPOSITORY_GRYPE
  - REPOSITORY_SECRETLINT
  - REPOSITORY_SYFT
  - REPOSITORY_TRIVY
  - REPOSITORY_TRIVY_SBOM
  - REPOSITORY_TRUFFLEHOG
  - SPELL_CSPELL
  - SPELL_LYCHEE
  - XML_XMLLINT
  - YAML_PRETTIER
  - YAML_V8R
  - YAML_YAMLLINT

## How to generate the flavor

Create a GitHub release on your repo, it will generate and publish your custom flavor using the MegaLinter custom Flavor Builder matching the tag name of your release (example: `9.0.0`)

You can also generate a custom flavor using MegaLinter Custom Flavor by pushing on any branch or manually run the workflow `megalinter-custom-flavor-builder.yml`.

## How to use the custom flavor

Follow [MegaLinter installation guide](https://megalinter.io/latest/install-assisted/), and replace related elements in the workflow.

- GitHub Action: On MegaLinter step in .github/workflows/mega-linter.yml, define `uses: nvuillam/megalinter-custom-flavor-npm-groovy-lint@main`
- Docker image: Replace official MegaLinter image by `ghcr.io/nvuillam/megalinter-custom-flavor-npm-groovy-lint/megalinter-custom-flavor:latest`