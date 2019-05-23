A customisable kubernetes admission webhook that can be used for admission

Primary user needs:
* Customisable admission via configuration
* Awareness of current cluster state

Google, MS, redhat, CBA, styra behind it

You declare constaints on the API server which will be enforced.

Examples:
All namespaces have a label that lists a point-of content
All pods must have an upper bound for resource usage
All images must be from an approved repository
Services must all have globally unique selectors

CRD: http://config.gatekeeper.sh/v1alpha

Audit:
Each constraints status is exposed on the status field of the CRD
any violations included there.

rego policy rules are typesafe, there's an openapi schema

v3 of gatekeeper allows you to just configure and pass a rego template
https://raw.githubusercontent.com/Azure/azure-policy/master/samples/KubernetesService/container-whitelisted-images/gatekeeperpolicy.rego

Potential growth:
Mutation
External data
Authorization - likely a separate project
More audit features
Metrics - rejections etc
Developer tooling - make reuse easy
Dry run

slack.openpolicyagent.org #kubernetes-policy
