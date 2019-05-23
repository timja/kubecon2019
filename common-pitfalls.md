Datadog:
Largest cluster over 2000 nodes
average is 1000-1500

Lessons learnt:
1. It's always DNS
Monitor your DNS errors
1.2 It's always DNS
under load ports aren't reused fast enough

2. Jobs are not starting, image pulls fail
DaemonSet crashloopbackoff, imagePullPolicy, caused rate limiting and prevented any image pulling
Fix: Admission webhook denying latest webhook - applied to pods which prevented new workloads from starting

3. I can't kubectl

4. DaemonSet resource limit issues with priority of critical

4. Log intake volume increased by 10x

6. Removing replica count in spec causes it to scale down to 1 replica

7. Cassandra broke
120 nodes deployed yesterday
Deployed fine
Broke next day
> 25% pods pending: Volume affinity issue
> 25% nodes had been deleted + local volumes bound to deleted nodes
Shortage of nodes in AZ, rebalanced during the night
Now different autoscale group in each zone

8. Slow deploy heartbeat
Deployments getting slower
Cause:
4000 pending pods
cronjob set to create a job every 10 minutes, had a wrong toleration applied and every loop of scheduler was considering the request, caused a big slowdown

9. Contained:
Broken runtime
#1
16000 zombie processes on machine
caused by redis readiness probe (shell script) with a really small timeout, and no supervisor in container so no reaping of zombie

#2
process blocked on IO couldn't be frozen by refridgerate process

#2.1 Performance issues
Symptoms:
Slow deployment
Pod took 1+mn to start

Cause:
Load on nodes running deployment high
Because IOs are being rate limited

Why:
DNS queries

An app started doing 5000+ dns queries per second
coredns logs filled the logs

10. Graceful termination
Queue consumer autoscaled on queue depth
On scale down, job must finish (hours)
 -> pod enters terminating status
 -> kube2idam refuses to fresh credentials
    -> fixed upstream
 -> kubelet restart cancels context
   -> fixed in containerd

Key take-aways
1. careful with daemonsets
2. dns is hard
3. cloud infra not transparent
4. containers not really contained


