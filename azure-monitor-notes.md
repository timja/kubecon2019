Live data not being scrollable being fixed next week
Next month ingesting prometheus metrics will be supported
Cluster health being re-worked, to be more obvious first and configurable after - currently you can use the learn more link in the top right to see what could be causing it
Builtin alerts functionality being added soon, i.e. named alerts PodRestartingTooMuch, then you only need to add thresholds and not the whole query, the doc is a stopgap measure as its one of their worst areas atm: https://docs.microsoft.com/en-us/azure/azure-monitor/insights/container-insights-analyze
The clusters monitor can show data from all subscriptions, it uses what you have configured in your global subscription filter
RBAC access coming later to filter who can see what (not soon)
The container info in the monitor is going to become live
Describe info being added
Security is a big focus atm, and they are trying to make sure all the data a developer needs to solve their problem can be found in Azure Monitor so they don't need direct access to the cluster via kubectl
If cluster onboarding to monitor fails then use this script here to find out why: https://github.com/Microsoft/OMS-docker/tree/ci_feature_prod/Troubleshoot#troubleshooting-script
If you still need help email: askcoin@microsoft.com
They would love any feedback, send to askcoin@microsoft.com
(usually reply same day / immediately)
The team is based in Redmond, 1 PM and 7 other team members

