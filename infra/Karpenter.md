pod_scheduler -> CA -> ASG -> Ec2
pod_scheduler -> Karpenter -> Ec2

nodepool types:

    single
    multi
    weighted

Batching:

    1 sec idol window to take the pods within 10 seconds and create a node for those instead of creating a node for each pod

Scheduling:

    pod resource requests ( tags can be added which will be automatically added to the nodes by karpenter )
    nodeSelector using lables
    nodeAffinity
    taints and tolerations
    topology spread
    pod_affinity and anti_affinity

Optimization:

    reducing the node of ec2 instances
    reducing the instance type
    consolidation = WhenUnderutilized

Can't run karpenter on node which is provisioned by karpenter.
prometheus + grafana setup since it emits the metrics
it will select the AMI from ASM parameter store

Drift:
    when there is a mismatch in provisioned and current config, it will update the nodes in a rolling deployment fashion
        latest ami version
        ami version based on eks version

Distruption:
    Select candidate -> Replace Candidate -> Drain candidate -> Delete condidate

    have control over
        you can add config to not distrupt a perticuler pod
        how many pods can distrupt at a time
        how speed the distruption can happen
    
    while taking the decision to find out the candidate it will try to focus on minimizing the pod distruption.
    it will consider whether the pod can be distrubed or not

Consolidation:
    N -> 0 consolidation ( no new nodes )
    N -> 1 consolidaiton ( new nodes will be created )