# GitHub Streak

## Overview

`github-streak` is a tiny repository to demonstrate automated daily commits to keep a GitHub contribution streak alive. The repository contains a scheduled GitHub Actions workflow that appends a timestamp to `streak.txt` every day.

## Features

- Automated daily commit to update `streak.txt` and keep contribution streaks active.
- Scheduled workflow to perform commits at UTC midnight.
- A separate scheduled workflow to update this `README.md` file on a specified date.

## Files

- `streak.txt` — receives an appended timestamp each day by the daily workflow.
- `.github/workflows/daily-streak-maintenance.yml` — appends a timestamp to `streak.txt` and pushes the change.
- `.github/workflows/update-readme-tomorrow.yml` — (scheduled) updates this README and commits it.

## How it works

1. The `daily-streak-maintenance` workflow runs on a daily schedule and appends the current UTC datetime to `streak.txt`.
2. The `update-readme-tomorrow` workflow (scheduled separately) will overwrite this `README.md` with a comprehensive project description and commit the change.

## Running Locally

To reproduce the daily update locally:

```bash
echo "$(date '+%Y-%m-%d %H:%M:%S') - Keeping the streak alive!" >> streak.txt
git add streak.txt
git commit -m "Local simulation: update streak.txt" || true
```

## Contributing

Contributions are welcome. Please open issues or pull requests on GitHub. If you're submitting changes that affect scheduled workflows, ensure the workflow permissions and commit messages are clear and include `[skip ci]` when appropriate.

## Notes

- The `update-readme-tomorrow` workflow is scheduled to run on Jan 5 at 00:05 UTC. It will run annually on that date; if you want a single-run action, consider manually removing or editing the workflow after it runs.
- Workflows that push commits use the `GITHUB_TOKEN` with `contents: write` permission.

## License

This repository is provided as-is. Update the license information here as needed.

