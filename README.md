# Test Run Env Job Keelson Namespace Only

E2E test repo for the `kubernetes-run-environment` build in buildon-github-actions.

Tests deployMode `job` with imageAutoUpdateProvider `keelson` under the
namespace-only permission model (`clusterScopedDelegation: parent`): the env's
cluster-scoped resources (from the vendor helm bundle) split out into the
separate on-behalf dir for the RP parent. The delegated-plus-sensitive combo
makes this the home for the sensitive-resource SIGN-OFF pass once its design
review lands. Also the only run repo with `cleanUpPolicy: enabled` (the rest
stay dryrun) and, being job mode, expects the suspended CronJob plus zero-scale
debug Deployment pair.

Consumed as a child by `test-run-platform-cluster-scoped-on-behalf`.

Pending notes:

- Uses draft schema fields (`clusterScopedDelegation`) from the uncommitted
  `spec-kaptainpm-schema` repo; the schema must be faked into the build before
  this repo can build.
- Sign-off configuration gets added here when the sign-off review pass
  settles; behaviour assertions get added to the hooks once the reference
  scripts land.
