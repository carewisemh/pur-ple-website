# Pur_Ple Website — Review Deployment

This repository currently contains a **single-page HTML review shell** for Pur_Ple (Purposeful People), based in Osun State, Nigeria. It is not yet the complete multi-page Next.js site.

## Current deployment

- Review URL: https://pur-ple-review.vercel.app
- Project: `pur-ple-review`
- Access protection: Vercel SSO enabled for all deployments
- Search indexing: blocked in HTML and `robots.txt`
- Online donations: disabled
- The current deployment serves the homepage only; paths such as `/about/`, `/programmes/`, `/impact/`, `/contact/`, `/privacy/` and `/donate/` have not been deployed.

## Full website package

The multi-page Next.js App Router package is supplied separately as `Pur_Ple_Website_Stage_4_Review.zip` in the project conversation. It contains 14 route files, local WebP image assets and a source-level test script (`npm run test:stage4`). That package has not yet been deployed to this Vercel project.

## Stage 4 release review

See [STAGE-4-TEST-AND-LAUNCH.md](./STAGE-4-TEST-AND-LAUNCH.md) for the smoke-test results, failed route checks, build limitation and launch blockers.

## Before public launch

1. Commit and deploy the full reviewed Next.js package and confirm the production build succeeds.
2. Test all routes, responsive layouts, keyboard navigation, links and accessibility.
3. Finalise and approve the privacy notice.
4. Confirm participant/guardian permissions and safeguarding clearance for all photographs, especially children’s images.
5. Confirm the final domain, canonical metadata, sitemap and social-sharing image.
6. Keep donations disabled until the recipient account and payment journey are configured and tested.
7. Remove review-only crawler restrictions only as part of the approved public launch.

Vercel reported that its GitHub integration must be installed before it can create a Git-linked project. The current review remains protected; it has not been approved as a public launch.
