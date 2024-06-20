# Code Coverage Action

A GitHub Action to process COBERTURA code coverage reports, generate summaries, add comments to pull requests, and fail the workflow if the coverage is below a specified threshold.

## Inputs

| Name                        | Description                                              | Required | Default                                |
|-----------------------------|----------------------------------------------------------|----------|----------------------------------------|
| `code_coverage_artifacts_name` | The name of the code coverage artifacts                  | false    |                                        |
| `coverage_directory`        | The directory to store the coverage results              | true     | `coverage`                             |
| `coverage_results_path`     | The path to the coverage results file                    | true     | `code-coverage-results.md`             |
| `minimum_coverage`          | The minimum acceptable code coverage percentage          | false    |                                        |
| `add_pr_comment`            | Add coverage comment to pull requests                    | false    | `true`                                 |
| `add_to_summary`            | Add coverage report to job summary                       | false    | `true`                                 |
| `delete_artifact`           | Delete the code coverage artifact after use              | false    | `true`                                 |

## Usage

To use this action in your workflow, add a step to call it with the appropriate inputs. Here is an example:

```yaml
jobs:
  code-coverage:
    runs-on: ubuntu-latest
    steps:
      - name: Use Code Coverage Action
        uses: KKica/code-coverage@v0.1.0
        with:
          code_coverage_artifacts_name: ${{ env.CODE_COVERAGE_ARTIFACTS_NAME }}
          coverage_directory: ${{ env.COVERAGE_DIRECTORY }}
          coverage_results_path: ${{ env.COVERAGE_RESULTS_PATH }}
          minimum_coverage: ${{ env.MINIMUM_COVERAGE }} # optional
          add_pr_comment: 'true' # optional
          add_to_summary: 'true' # optional
          delete_artifact: 'true' # optional
