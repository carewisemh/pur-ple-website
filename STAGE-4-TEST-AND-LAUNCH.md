# Pur_Ple Website — Stage 4: Test and Launch Review

**Review date:** 25 October 2026  
**Decision:** Public launch blocked pending fixes and approvals.

## Summary

The current Vercel review deployment is healthy at the hosting level, but it is not the complete multi-page website. It contains a one-page static review homepage and `robots.txt`. The separate Next.js Stage 2 package has passed source-level checks, but its dependencies could not be installed in this environment, so a production build and browser end-to-end run have not yet been completed.

The review deployment remains protected by Vercel Authentication (SSO). Online donations remain disabled. Search indexing is blocked for the review build.

## Live deployment checks

| Check | Result | Evidence |
|---|---|---|
| Homepage response | PASS | `https://pur-ple-review.vercel.app/` returned HTTP 200. |
| Search crawler block | PASS | `/robots.txt` returned HTTP 200 with `User-agent: *` and `Disallow: /`; HTML has a `noindex` meta tag. |
| Main-section anchors | PASS | All local section links on the review homepage resolve to an existing element ID. |
| Contact details | PASS | Email, WhatsApp, Instagram and community sign-up link are present. |
| Donation safety | PASS | No payment form or checkout is present; the page states that online donations are disabled. |
| Runtime errors | PASS | Vercel reported no runtime errors for the selected 24-hour scan window. |
| Deployment state | PASS | Vercel reports deployment `dpl_C7CQhtkTCZ5asX9YGurdATcdazsm` as `READY`. |
| Access protection | PASS | The `pur-ple-review` project has Vercel SSO protection enabled for all deployments. |
| Multi-page routes | FAIL | `/about/`, `/programmes/`, `/impact/`, `/get-involved/`, `/contact/`, `/privacy/` and `/donate/` each returned HTTP 404. The current deployed artifact is not the complete Next.js app. |

## Stage 2 package checks

The added `npm run test:stage4` source-level check passed **7 checks with 0 failures**:

- All 14 expected route files are present in the Next.js source package.
- All 17 unique referenced local image paths resolve to assets in `public/images/`.
- Review crawler blocking is configured.
- Online giving remains disabled.
- The privacy notice is explicitly labelled as a draft.
- Quivers Christmas Party attribution now matches the approved brief: Pur_Ple organised it.
- The production build script is present.

The existing TypeScript/TSX source check with local stubs also completed without diagnostics. This is not equivalent to a full dependency-backed typecheck.

**Build limitation:** `npm install --no-audit --no-fund` timed out and did not install dependencies. `npm run build` therefore could not start (`next: not found`). A full Next.js production build has not been verified.

## Public-launch blockers

1. **Deploy the complete application.** The Vercel project currently serves only the one-page HTML review site. The 14-route Next.js implementation and its assets must be deployed and retested before release. Vercel reported that the GitHub integration must be installed before it can create a Git-linked deployment.
2. **Approve the privacy notice.** The website privacy notice remains explicitly marked as a draft. Pur_Ple needs to verify data-handling practices, contact details, the external sign-up service and applicable requirements before approving final wording.
3. **Clear photography permissions and safeguarding.** The full package references identifiable photographs, including images of children. Confirm the relevant participant/guardian permissions and safeguarding checks, or remove any uncleared images before publication.
4. **Run release tests.** After the full app is deployed, run `npm install`, `npm run build`, browser tests for all routes, mobile/keyboard checks, link checks and a final content review. The current live multi-route test is not passing.
5. **Prepare public indexing and domain settings.** Keep crawler blocking in place for review. Only after approval, configure the final domain, canonical metadata, sitemap and social-sharing image, then intentionally revise indexing controls.
6. **Keep online donations disabled.** Do not add payment details until the recipient account and payment flow are set up, verified and successfully tested.

## Release decision

**Do not remove SSO protection or treat this deployment as the public launch.** The first-page smoke test passes, but required pages return 404 and the full Next.js production build is unverified. Public launch can be reconsidered after blockers 1–4 are cleared and the complete deployment passes its end-to-end checks.
