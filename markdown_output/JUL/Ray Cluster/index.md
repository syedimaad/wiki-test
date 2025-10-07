Create cluster

bashblazectl cluster create \--name \<cluster name\> -n us-labs \\
\--head-node m6a.2xlarge \--default-workers-node g5.24xlarge \\
\--default-workers-count 1 \--default-workers-gpu

Delete cluster

blazectl cluster delete \--name \<cluster name\> -n us-labs

Show running clusters

bashkubectl get pods -n us-labs

\
Install

bashpip install blazectl

<https://github.com/blaze-cluster/blaze-ctl>\
configure kube\
Josh RecSys Cluster\
