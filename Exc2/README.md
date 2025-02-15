```sh
stepandilman@Stepans-MacBook-Pro-2 architecture-sprint-6 % kubectl get all
NAME                                       READY   STATUS    RESTARTS   AGE
pod/test-app-deployment-66ff667f5f-45rt9   1/1     Running   0          76s
pod/test-app-deployment-66ff667f5f-4vvl2   1/1     Running   0          5m55s

NAME                       TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)    AGE
service/kubernetes         ClusterIP   10.96.0.1     <none>        443/TCP    30h
service/test-app-service   ClusterIP   10.110.27.4   <none>        8080/TCP   23m

NAME                                  READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/test-app-deployment   2/2     2            2           23m

NAME                                             DESIRED   CURRENT   READY   AGE
replicaset.apps/test-app-deployment-66ff667f5f   2         2         2       5m55s
replicaset.apps/test-app-deployment-7d4c78bb59   0         0         0       23m

NAME                                               REFERENCE                        TARGETS           MINPODS   MAXPODS   REPLICAS   AGE
horizontalpodautoscaler.autoscaling/test-app-hpa   Deployment/test-app-deployment   memory: 66%/80%   1         10        2          23m
stepandilman@Stepans-MacBook-Pro-2 architecture-sprint-6 % kubectl get events --field-selector involvedObject.kind=HorizontalPodAutoscaler --sort-by=.lastTimestamp
LAST SEEN   TYPE      REASON                         OBJECT                                 MESSAGE
71m         Warning   FailedGetScale                 horizontalpodautoscaler/test-app-hpa   Unauthorized
22m         Warning   FailedGetResourceMetric        horizontalpodautoscaler/test-app-hpa   failed to get cpu utilization: did not receive metrics for targeted pods (pods might be unready)
22m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/test-app-hpa   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: did not receive metrics for targeted pods (pods might be unready)
20m         Warning   FailedComputeMetricsReplicas   horizontalpodautoscaler/test-app-hpa   invalid metrics (1 invalid out of 1), first error is: failed to get cpu resource metric value: failed to get cpu utilization: missing request for cpu in container test-app of Pod test-app-deployment-7d4c78bb59-96gdt
7m54s       Warning   FailedGetResourceMetric        horizontalpodautoscaler/test-app-hpa   failed to get cpu utilization: missing request for cpu in container test-app of Pod test-app-deployment-7d4c78bb59-96gdt
84s         Normal    SuccessfulRescale              horizontalpodautoscaler/test-app-hpa   New size: 2; reason: memory resource utilization (percentage of request) above target
stepandilman@Stepans-MacBook-Pro-2 architecture-sprint-6 % 
```


[dashboard](dashboard.png)