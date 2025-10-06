# MegaLinter Custom Flavor: npm-groovy-lint

This custom MegaLinter aims to have an optimized Docker image size.

It is built from official MegaLinter images, but is maintained on https://github.com/nvuillam/megalinter-custom-flavor-npm-groovy-lint by Nicolas Vuillamy

## Embedded linters

  - [DOCKERFILE_HADOLINT](https://megalinter.io/latest/descriptors/dockerfile_hadolint/)
  - [GROOVY_NPM_GROOVY_LINT](https://megalinter.io/latest/descriptors/groovy_npm_groovy_lint/)
  - [JAVASCRIPT_PRETTIER](https://megalinter.io/latest/descriptors/javascript_prettier/)
  - [JSON_JSONLINT](https://megalinter.io/latest/descriptors/json_jsonlint/)
  - [JSON_NPM_PACKAGE_JSON_LINT](https://megalinter.io/latest/descriptors/json_npm_package_json_lint/)
  - [JSON_PRETTIER](https://megalinter.io/latest/descriptors/json_prettier/)
  - [JSON_V8R](https://megalinter.io/latest/descriptors/json_v8r/)
  - [MARKDOWN_MARKDOWNLINT](https://megalinter.io/latest/descriptors/markdown_markdownlint/)
  - [MARKDOWN_MARKDOWN_TABLE_FORMATTER](https://megalinter.io/latest/descriptors/markdown_markdown_table_formatter/)
  - [REPOSITORY_CHECKOV](https://megalinter.io/latest/descriptors/repository_checkov/)
  - [REPOSITORY_GITLEAKS](https://megalinter.io/latest/descriptors/repository_gitleaks/)
  - [REPOSITORY_GIT_DIFF](https://megalinter.io/latest/descriptors/repository_git_diff/)
  - [REPOSITORY_GRYPE](https://megalinter.io/latest/descriptors/repository_grype/)
  - [REPOSITORY_SECRETLINT](https://megalinter.io/latest/descriptors/repository_secretlint/)
  - [REPOSITORY_TRIVY](https://megalinter.io/latest/descriptors/repository_trivy/)
  - [REPOSITORY_TRUFFLEHOG](https://megalinter.io/latest/descriptors/repository_trufflehog/)
  - [SPELL_CSPELL](https://megalinter.io/latest/descriptors/spell_cspell/)
  - [SPELL_LYCHEE](https://megalinter.io/latest/descriptors/spell_lychee/)
  - [XML_XMLLINT](https://megalinter.io/latest/descriptors/xml_xmllint/)
  - [YAML_PRETTIER](https://megalinter.io/latest/descriptors/yaml_prettier/)
  - [YAML_V8R](https://megalinter.io/latest/descriptors/yaml_v8r/)
  - [YAML_YAMLLINT](https://megalinter.io/latest/descriptors/yaml_yamllint/)

## How to use the custom flavor

Follow [MegaLinter installation guide](https://megalinter.io/latest/install-assisted/), and replace related elements in the workflow.

- GitHub Action: On MegaLinter step in .github/workflows/mega-linter.yml, define `uses: nvuillam/megalinter-custom-flavor-npm-groovy-lint@main`
- Docker image: Replace official MegaLinter image with `ghcr.io/nvuillam/megalinter-custom-flavor-npm-groovy-lint/megalinter-custom-flavor:latest`

## How the flavor is generated and updated

This custom flavor is automatically kept up to date with MegaLinter releases:

1. **Automatic version sync**: The `check-new-megalinter-version` workflow runs daily, checks for new MegaLinter releases, and automatically creates matching releases in this repository.

2. **Automated builds**: Each release triggers the `megalinter-custom-flavor-builder` workflow, which:
   - Builds a Docker image with only the selected linters
   - Publishes to GitHub Container Registry (ghcr.io)
   - Optionally publishes to Docker Hub (if credentials are configured)

3. **Available image tags**:
   - Release tags (e.g., `v9.0.0`): Built from MegaLinter releases
   - `beta` tag: Built from non-main branch pushes for testing
   - `latest` tag: Points to the most recent release

## Configuration requirements

### Required: Personal Access Token

For automatic version checking to work, a `PAT_TOKEN` secret must be configured with:
- Contents: Read and write
- Actions: Read and write

See the [Custom Flavors documentation](https://megalinter.io/beta/custom-flavors/) for detailed setup instructions.

### Optional: Docker Hub publishing

To publish to Docker Hub in addition to ghcr.io, configure:
- `DOCKERHUB_REPO` variable (e.g., your Docker Hub username)
- `DOCKERHUB_USERNAME` secret
- `DOCKERHUB_PASSWORD` secret

## How to generate the flavor manually

If you need to manually trigger a build:

1. **Create a GitHub release**: Creates a versioned build matching the tag name (e.g., `v9.0.0`)
2. **Push to any branch** (except main): Builds a `beta` tagged image for testing
3. **Manually run the workflow**: Go to Actions > Build & Push MegaLinter Custom Flavor > Run workflow

See [full Custom Flavors documentation](https://megalinter.io/beta/custom-flavors/).

## How to use the custom flavor

Follow [MegaLinter installation guide](https://megalinter.io/latest/install-assisted/), and replace related elements in the workflow.

- **GitHub Action**: On MegaLinter step in `.github/workflows/mega-linter.yml`, define `uses: nvuillam/megalinter-custom-flavor-npm-groovy-lint@main`
- **Docker image**: Replace official MegaLinter image with `ghcr.io/nvuillam/megalinter-custom-flavor-npm-groovy-lint/megalinter-custom-flavor:latest`

[![MegaLinter is graciously provided by OX Security](https://raw.githubusercontent.com/oxsecurity/megalinter/main/docs/assets/images/ox-banner.png)](https://www.ox.security/?ref=megalinter)
