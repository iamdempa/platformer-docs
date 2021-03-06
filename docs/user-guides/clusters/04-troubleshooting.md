---
id: 04-troubleshooting
title: Troubleshooting cluster connections
sidebar_label: Troubleshooting cluster connections
slug: troubleshooting
---

## My Cluster shows up as 'Disonnected' on the Platformer Console.

### If you just installed the Agent and the Cluster has never connected before

This usually is an indication that your Cluster does not have access to the internet or the Agent pod does not have access to the internet due to a problem with your cluster's internal network setup.

1. Ensure that Pods in your cluster can reach the public internet.<br/>
   Run a wget command from a busybox pod<br/>

    ```bash
    kubectl run busybox --namespace=platformer-system --image=busybox --restart=Never --rm -it -- sh
    ```

    Once inside the Pod run `$ wget -O- platformer.com` to see if it produces an ouput.

2. Ensure that there are no firewall rules or network security policies preventing the Agent pod from connecting to the Platformer APIs.

3. The Agent Pod's logs may shed some light into the issue as well. <br/>

    Copy the **Project ID** of the project the cluster is connected to using **Admin Panel** > **Project Settings** > **General** (Project ID field).

    ```bash
    export PROJECT_ID=<insert Project ID here>
    export AGENT=$(kubectl get pod -n platformer-system -l project=$PROJECT_ID --no-headers -o custom-columns=":metadata.name")
    kubectl logs -n platformer-system $AGENT
    ```

4. Reinstall the agent (the kubectl command can be found in the Cluster page on the Console).

5. If all else fails, contact [Platformer Support](https://platformer.atlassian.net/servicedesk/customer/portal/1).

### If your Cluster has been connected before but now shows up as disconnected

The Platformer Agent will automatically reconnect in almost all scenarios, but it is possible for some extended network interference to cause it to permenantly disconnect.

1. The quickest way to resolve a disconnected agent is to restart the Agent pod in the `platformer-system` namespace.

    ```bash
     kubectl delete pods -n platformer-system --all
    ```

    Allow the agent pod upto 2 minutes to initialize and reconnect.

2. If the above step does not work, refer to steps 2-5 in the section above.
