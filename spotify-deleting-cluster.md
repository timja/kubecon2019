How spotify accidentally delete prod clusters twice, with minimal user impact

Spotify uses GCP
Use GKE

All stateless backend services getting migrated to GKE

3 prod clusters one in each main region, all getting backed up every hour (europe, asia, usa)

Wrong tab, clicked delete, :facepalm: deleted 50 node prod cluster running lots of workloads

Took 3 hr 25 min to restore

bugs in cluster creation scripts that weren't run too often
Docs incomplete and incorrect

Cluster creation process not resumable, every error meant starting from the beginning

Decided to change to terraform to define the infra as code

did an import for the asia cluster in a PR didn't merge it yet
Merged a separate PR that didn't have the asia cluster defined
Asia cluster deleted

Merged the asia cluster PR
Creation failed because not enough permissions
Gave permissions
Reran - didn't reimport state though
Terraform now knew about the USA cluster but it wasn't in the state properly, deleted.

Impact:
scale vms
update master ip hardcoding in manual
everyone had to refresh the kubectl config file

What they did right:
planned for failure from day 1
migrated applications gradually
they have a culture of learning

plan for failure:
recommended each team only migrate services partially for k8s
failover to non k8s
didn't register services the normal way

used pod IPs not service IP (interoperability reasons)
polls service IPs then updates service discovery

Best practices:
backed up our clusters
codified their infrastructure
performed dr tests
made team members practice them

codified:
introduced new toosls gradually
added linters and validators
added the output of the dry run as a comment to the pull request
required status checks to pass before merging
required feature branch to be up to date

DR tests:
record any issues and fix them as you go
schedule them regularly

practice:
second delete took ~9 hours to recover from over night
now can restore in under 1 hour

culture of learning not blame

K8s at spotify:
"GA" at spotify, everything is allowed to be run there now including mission critical software
