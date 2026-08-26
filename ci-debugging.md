# CI Debugging Notes

Quick things I keep coming back to when a pipeline mysteriously fails.

## GitHub Actions

- Set `ACTIONS_STEP_DEBUG=true` as a repo secret or workflow variable to get step-level debug output.
- Upload artifacts with `if: always()` so logs are available even after a failed job.
- On self-hosted runners, run `df -h` before blaming the YAML.

## Jenkins

- Grab console logs faster:
  `curl -u user:token "$JENKINS_URL/job/$JOB/$BUILD_NUMBER/consoleText"`
- A stuck pipeline can sometimes be unstuck from the script console via `Jenkins.instance.getItemByFullName("job").getBuildByNumber(n)`.

## General

- If a test only fails in CI, try capturing the random seed and rerun locally with the same seed.
- Print the environment before running tests: `env | sort`.

More tinkering notes soon.