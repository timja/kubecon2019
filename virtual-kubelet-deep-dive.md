virtual kubelet is just a thing that pretends to be a kubelet
It doesn't talk to the container runtime, but talks to a provider instead

provider:
conforms to the current api provided by virtual kubelet
it doesn't have direct access to the k8s api

current providers:
alibaba
azure - aci
azure - iot edge
aws
hashicorp nomad
huawei
openstack stun

alibaba: "Viking"
they offer public cloud product: Serverless Kubernetes
https://www.alibabacloud.com/help/doc-detail/94078.html

https://github.com/virtual-kubelet/virtual-kubelet
https://github.com/Azure/iot-edge-virtual-kubelet-provider
Moving providers out of tree soon
1.0 release should be coming this week

#virtual-kubelet in Kubernetes slack
It is a CNCF sandbox project

