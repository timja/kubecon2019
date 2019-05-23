Buildkit

Has 2 special mount points for RUN:
cache
secret

huge performance benefits if you're building in docker

Building images in kubernetes:
https://github.com/moby/buildkit/blob/master/docs/rootless.md

Doesn't need a service, internally runs kubectl exec
Some implications around security

export BUILDKIT_HOST=kubectl://...
buildkit build..

docker buildx is the next generation cli for intergrating buildkit to docker

supports multi arch images and "bake" compose like building for images

remote cache:
registry or shared FS
similar to --cache-from but more chance of hitting cache

Consistent hashing (same pod name)
Stateful set
Build will always hit the same daemon and get the same cache
Caveats:
High I/O overhead

If you have a fast cache registry it may be better
If you don't want to have this then consistent hashing can work too

CRD
Container builder interface
The first common CRD for building
Now being deprecated (CBI)

Tekton is the new one, spun out from knative
tekton.dev/v1alpha1

buildkit can be specified as a task

Buildkit is fast and secure

github.com/moby/buildkit
