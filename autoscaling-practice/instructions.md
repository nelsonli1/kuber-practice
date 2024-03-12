# Instructions

After applying the `php-apache.yaml` file using `kubectl apply -f php-apache.yaml` run `kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10` to manually create / adjust the autoscaling of the cluster.

Use `kubectl get hpa` to see how much load the pod is using.

## Increasing the load

Run this in a separate terminal so that the load generation continues and you can carry on with the rest of the steps

```
kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"
```

This should repeated print out `OK!`. To terminate this process, press `<Crtl> + C`

To watch if the pod is autoscaling, use `kubectl get hpa php-apache --watch`. This will print out details about the `php-apache` deployment while it is using more CPU power and increasing its number of replicas.

## Alternative

Instead of running the command `kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"` we can use the `hpa-v2.yaml` file which specifies a Horizontal Pod Autoscaler for Kubernetes. We can simply run `kubectl apply -f hpa-v2.yaml` and it will autoscale.
