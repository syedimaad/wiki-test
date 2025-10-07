What monitoring tools we use for ES on ECK -

- Grafana -
  [[http://monitoring.myjosh.in/grafana](http://monitoring.myjosh.in/grafana/login)]{.underline}
  in ECK org. We've created 2 dashboards one for pod level metrics &
  other one for node level

- ECK monitoring cluster for stack monitoring - We use its Kibana

[<https://prod-monitoring-kibana-eck.myjosh.in:5601/>]{.underline} Pls
login with respective password & navigate to Stack monitoring option in
hamburger menu on top left. There based on the no. of nodes or the no.
of indices we identify the ES cluster & click on the name (all clusters
have the name elasticsearch only for now as per the service). Inside
we'll see *overview* tab for cluster level metrics, *nodes* for node
level metrics

- Also we've created customized dashboards per cluster for some
  important metrics. This can be viewed in the hamburger menu \>\>
  Dashboard \>\> Cluster metrics \>\> Cluster name (pls select this in
  the drop down besides the search bar)

- Cerebro - Its a UI tool to visualise the current shard level metrics &
  configs. Since currently we don't have any auth in the ES clusters,
  via cerebro, you'll be able to perform index level or shard level
  operations also. Pls use this link for cerebro. This doesn't have
  access to prod

[<http://172.20.74.159:7501/#/connect>]{.underline}

There you can add the link of the respective ES cluster to monitor
