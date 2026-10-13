# Reusable workflows — verified course completion

This repository is an attributed copy of [GitHub Skills Create and use reusable workflows](https://github.com/skills/reusable-workflows). Instructor game, assets, and deployment workflow are course practice, not an original showcase. Instructor [MIT license](LICENSE) is preserved.

Completed 2026-10-13 through GitHub connectors and hosted Actions runners. No Codespace, VS Code terminal, or local development environment was used. The supervising agent operated Chrome only for Pages configuration and live-site audit. No custom secrets, paid compute, backend, or custom domain was introduced.

## Caller and callee execution

- Created `.github/workflows/reusable-node-quality.yml` on branch `reusable-workflows`, commit `04f8c51888ead917e48aa8a23f061e0ef8c0ac21`. Its workflow_call input defaults Node to 20; the caller explicitly passes Node 24.
- Added `.github/workflows/ci.yml`, commit `08fa339a0fc2efc8eeb5ec1c70411c5713e19d4e`. [Initial CI run 38441330898](https://github.com/Khemology/skills-reusable-workflows/actions/runs/38441330898) successfully executed caller/callee Lint, Tests with Coverage, and E2E Tests with Playwright.
- A real instructor Step 2 check initially failed its exact workflow-name check: Markdown code-block extraction retained three outer spaces. Actionlint and actual CI accepted the YAML; the teacher name check was text-sensitive. Commit `4cbe6b9c1665282f03338bf10c8e7cd648736a11` removed outer indentation; teacher checks subsequently passed. This was a course-check failure, not a failed application test.
- Added deployment and PR-output comment jobs, commit `3e8c337c0457a0ee68e30f0528bd49166a823f94`.
- [Final CI run 38441754187](https://github.com/Khemology/skills-reusable-workflows/actions/runs/38441754187) completed successfully with all six jobs: quality Lint; quality Tests with Coverage; quality E2E Tests with Playwright; Pages build; Pages deploy; Comment on PR.
- [Vitest job 115449826247](https://github.com/Khemology/skills-reusable-workflows/actions/runs/38441754187/job/115449826247) logs show 5 test files and 33 tests passed. Aggregate coverage: 96.7% statements, 94.54% branches, 100% functions, 100% lines. Coverage configuration excludes setup files, entrypoint, and branding.
- [Playwright job 115449826307](https://github.com/Khemology/skills-reusable-workflows/actions/runs/38441754187/job/115449826307) logs show 6 Chromium tests passed against the runner localhost Vite development server. These tests were not executed against the deployed Pages URL.

## Permissions, deployment, and output

The supervising agent enabled Pages source GitHub Actions after reviewing instructor public static content, endpoint, and permissions. No custom domain; HTTPS enforced.

Quality jobs use contents read. The caller deployment job grants contents read, pages write, and id-token write to the instructor reusable deployment workflow. That callee builds `dist` with base `/skills-reusable-workflows/`, uploads a Pages artifact, deploys it, and exposes page_url. The caller comment job has pull-requests write and consumes that output. No custom secrets are passed.

[Deployment job 115450343704](https://github.com/Khemology/skills-reusable-workflows/actions/runs/38441754187/job/115450343704) logs report deployment success and setting page_url. [Comment job 115450446979](https://github.com/Khemology/skills-reusable-workflows/actions/runs/38441754187/job/115450446979) succeeded. The [actual PR comment](https://github.com/Khemology/skills-reusable-workflows/pull/2#issuecomment-6151711476) contains the returned [live Pages URL](https://khemology.github.io/skills-reusable-workflows/) and the correct CI run URL.

## Independent deployed-site audit

The supervising agent independently opened the live Pages site and observed 16 cards and game rules. It flipped Jetpacktocat then Class Act; after waiting, Moves was 1 and health was 19/20. Clicking New Game reset Moves to 0 and health to 20/20. This proves deployed-site load, card interaction, mismatch update, and reset. It is not exhaustive gameplay testing. The supervising agent also independently fetched the 33-test Vitest and 6-test Playwright logs.

## Completion and limits

[Teaching issue #1](https://github.com/Khemology/skills-reusable-workflows/issues/1) is closed as completed. [Instructor finish comment](https://github.com/Khemology/skills-reusable-workflows/issues/1#issuecomment-6151725115) confirms completion. After the final CI succeeded, [PR #2](https://github.com/Khemology/skills-reusable-workflows/pull/2) merged using expected head `3e8c337c0457a0ee68e30f0528bd49166a823f94`; merge commit `a9ab094c6b550fc7ee367a8311a5e550e91f1067`.

This proves same-repository workflow reuse, actual quality-job delegation, permission scoping, static deployment, and reusable output consumption. It does not prove cross-repository execution, deeper nested reusable chains, deliberately denied permission recovery, production AI architecture, or exhaustive security validation. No such claims are made. The instructor PR workflow publishes a shared Pages endpoint on PR changes; it is a training configuration, not a production deployment policy.
