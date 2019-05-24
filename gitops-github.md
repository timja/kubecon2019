gitops to manage github orgs

use kubernetes reconcilation loop
declared state -> observed state

declare members -> observed members -> invite, promote, remove members
repeat for metadata, teams, etc

called peribolos
https://github.com/kubernetes/test-infra/tree/master/prow/cmd/peribolos

design:
dump current org status to file
manage org metadata

docker run gcr.io/k8s-prow/peribolos --help
CI job:
https://github.com/kubernetes/test-infra/tree/master/config/jobs/kubernetes/org

enforce standard through CI tests
code review allows delegation of privileges
Pony GIFs to welcome you to the org 

has a proxy to cache github responses to protect from api usage rate limiting

problems:
people change usernames
alicesmith11102 -> alice accidentally remove alice, and can't add alicesmith, blows up peribolos

kubernetes org:
https://github.com/kubernetes/org/ @cblecker and @fejta

#sig-contrixex, #sig-testing, #prow

terraform git provider was looked at, problems of introducing terraform wouldn't have worked well with kubernetes
this allows writing yaml rather than hcl

