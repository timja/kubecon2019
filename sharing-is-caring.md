multi tenanted cluster, how to share

a namespace is a virtual cluster

use case 1: one team per cluster
pros:
self sufficient
less security risks maybe

cons:
in-efficient, bad utilisation
difficult to maintain coherence

use case 2: 
pros:
efficient compute

cons:
difficult to manage security
if there's controls can be hard for developers to move quickly

namespace options:
per team
per environment
per business unit
per git branch
per app

manage in gitops:
quota sizes,
contact details

cluster policies:
who can access the cluster
infra security, privileged pods etc
cluster size
cluster config - common things to install etc

namespace:
namespace access
app security - any ns policies
namespace quota
namespace config

security boundaries:
rbac
pod security policies
network policies
image policies
label policies

quota enforcement:
cpu
memory
storage
objects

2 admission controller:
mutating admission
validating admission

structuring your organisation against your infra:
developers want freedom vs operators want control
developers want self service and as quickly as possible
interaction between groups often with tickets

How? Use OPA (open policy agent)

