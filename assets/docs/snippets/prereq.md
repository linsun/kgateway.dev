1. Follow the [Get started guide](/docs/quickstart/) to install kgateway.

2. Follow the [Sample app guide](/docs/operations/sample-app/) to create an API gateway proxy with an HTTP listener and deploy the httpbin sample app.

3. Get the external address of the gateway and save it in an environment variable.
   {{< tabs items="Cloud Provider LoadBalancer,Port-forward for local testing" >}}
   {{% tab %}}
   ```sh
   export INGRESS_GW_ADDRESS=$(kubectl get svc -n kgateway-system http -o jsonpath="{.status.loadBalancer.ingress[0]['hostname','ip']}")
   echo $INGRESS_GW_ADDRESS  
   ```
   {{% /tab %}}
   {{% tab  %}}
   ```sh
   kubectl port-forward deployment/http -n kgateway-system 8080:8080
   ```
   {{% /tab %}}
   {{< /tabs >}}