# Install a Self-Hosted Runner

1. Go to your repository on GitHub.
2. Click on Settings > Actions > Runners.
3. Click New self-hosted runner.
4. Follow the instructions to download and configure the runner for your operating system.

For macOS, the commands will look like this:

## Download

```shell
# Download
mkdir ~/github-actions-runner && cd ~/github-actions-runner
curl -o actions-runner-osx-arm64-2.329.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.329.0/actions-runner-osx-arm64-2.329.0.tar.gz
tar xzf ./actions-runner-osx-arm64-2.329.0.tar.gz
```

## Install

```shell
cd ~/github-actions-runner
./config.sh --url https://github.com/<your-org-or-user>/<your-repo> --token <your-runner-token>
```

## Run

```shell
cd ~/github-actions-runner
./run.sh
```

## Update the Workflow to Use the Self-Hosted Runner

Modify the runs-on key in your workflow to use the self-hosted runner:

```yaml
jobs:
  prepare_release:
    runs-on: self-hosted
```