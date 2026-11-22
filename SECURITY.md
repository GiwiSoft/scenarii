# Security policy

Scenarii runs scheduled checks, stores credentials and API tokens, and exposes a dashboard and REST API. Security reports about the server, CLI, runner, container image or release pipeline are welcome and handled in private.

## Report a vulnerability

Do not open a public issue, discussion or pull request for a suspected vulnerability.

Preferred channel: **GitHub private vulnerability reporting**

<https://github.com/GiwiSoft/scenarii/security/advisories/new>

Email: **security@giwi.fr**

Include, when possible:

- affected version, tag or commit;
- how Scenarii is deployed (bare Node.js, container, reverse proxy, database);
- steps to reproduce, with a minimal scenario or request;
- observed impact and who can trigger it;
- any planned public disclosure date;
- a safe way to contact you.

GitHub Security Advisories is the private channel for the report and the fix. We use it to discuss the issue, prepare the patch and publish a coordinated advisory when a fixed release is available. If you report by email, we will open a private advisory to keep the thread and the eventual disclosure together.

## Scope

In scope:

- the server, REST API, dashboard and WebSocket endpoints;
- session handling, local passwords, password recovery, TOTP, OIDC and API tokens;
- API token scopes and permission checks;
- webhook signature verification and CI trigger rules;
- the CLI, scheduler, runner, scenario parser, variable interpolation and secret handling;
- the published container image and release artifacts;
- dependencies and build/release configuration when they create an exploitable path in Scenarii.

Out of scope:

- vulnerabilities in the sites or APIs that a scenario tests;
- third-party services such as GitHub, Telegram, Slack, Discord, mail providers or OIDC providers;
- a host, reverse proxy, TLS terminator or `settings.yaml` that is misconfigured or publicly exposes secrets;
- weak administrator passwords or a compromised administrator account;
- issues that require root access to the host;
- unsupported releases, forks and images rebuilt outside this repository;
- volumetric denial of service against your own deployment. Resource exhaustion reachable through normal authenticated use is still worth reporting.

Test only against an instance you own or are authorised to test. Do not access, modify or retain data that is not yours.

## Supported versions

| Version | Security support |
| --- | --- |
| Latest `1.x` release | Supported |
| Previous `1.x` minor | Security fixes for 90 days after the next minor is released |
| Older `1.x`, `0.x`, forks and custom images | Not supported |

Use the latest release from [GitHub releases](https://github.com/GiwiSoft/scenarii/releases) or the `latest` container tag. Security fixes are shipped as patch releases. Upgrade before reporting an issue that is already fixed on the latest release.

The current release line is visible on the releases page; this file does not need to change for every patch.

## Response times

These targets are indicative, not a contractual service level:

| Step | Target |
| --- | --- |
| Acknowledge the report | 3 business days |
| Initial assessment and severity | 7 calendar days |
| Critical fix | 30 days |
| High fix | 60 days |
| Moderate fix | 90 days |
| Low severity | Next scheduled release |
| Status update to the reporter | At least every 14 days |

Complex issues may need more time. We will say so, explain the blocker and agree on a revised date with the reporter.

## Coordinated disclosure

We follow coordinated disclosure:

- the report and discussion stay private until a fix is available;
- the default embargo is **90 days** from the report, or the release of the fix, whichever comes first;
- we may publish earlier when the issue is publicly known or actively exploited;
- the advisory is published through GitHub Security Advisories, with affected versions, impact, credit and upgrade instructions;
- we will credit the reporter unless they prefer to stay anonymous.

We do not run a paid bug bounty.

## CRA alignment

These practices support the vulnerability-handling expectations of the EU Cyber Resilience Act (Regulation (EU) 2024/2847): a private reporting channel, coordinated disclosure, defined supported versions, dependency monitoring and a machine-readable SBOM.

Scenarii is open-source software. This policy describes the project's handling process; it is not a declaration of CRA conformity for a product that embeds it.

## Supply chain

- Dependabot alerts and security updates are enabled for the repository.
- Dependencies are updated through reviewed pull requests and the test suite must pass before merge.
- CI generates a CycloneDX SBOM (`sbom.cdx.json`), published as a build artifact and attached to tagged releases.
- Container images are published with SBOM and provenance attestations.
- Release artifacts and container tags are built by the repository's GitHub Actions workflow.

## Good-faith research

We will not pursue legal action for good-faith research that follows this policy, stays within scope and avoids privacy violations, data destruction or service disruption. If you are unsure whether a test is allowed, ask first through the private advisory.
