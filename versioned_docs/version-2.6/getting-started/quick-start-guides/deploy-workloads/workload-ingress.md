---
title: Workload with Ingress Quick Start
---

<head>
  <link rel="canonical" href="https://ranchermanager.docs.rancher.com/getting-started/quick-start-guides/deploy-workloads/workload-ingress"/>
</head>

### Prerequisite

You have a running cluster with at least 1 node.

### 1. Deploying a Workload

You're ready to create your first Kubernetes [workload](https://kubernetes.io/docs/concepts/workloads/). A workload is an object that includes pods along with other files and info needed to deploy your application.

For this workload, you'll be deploying the application Rancher Hello-World.

1. Click **☰ > Cluster Management**.
1. Go to the cluster that you created and click **Explore**.
1. Click **Workload**.
1. Click **Create**.
1. Click **Deployment**.
1. Enter a **Name** for your workload.
1. From the **Container Image** field, enter `rancher/hello-world`. This field is case-sensitive.
1. Click **Add Port** and `Cluster IP` for the `Service Type` and enter `80` in the **Private Container Port** field. You may leave the `Name` blank or specify any name that you wish. Adding a port enables access to the application inside and outside of the cluster. For more information, see [Services](../../../pages-for-subheaders/workloads-and-pods.md#services).
1. Click **Create**.

**Result:**

* Your workload is deployed. This process might take a few minutes to complete.
* When your workload completes deployment, it's assigned a state of **Active**. You can view this status from the project's **Workloads** page.

### 2. Expose The Application Via An Ingress

Now that the application is up and running, it needs to be exposed so that other services can connect.

1.  Click **☰ > Cluster Management**.
1.  Go to the cluster that you created and click **Explore**.

1.  Click **Service Discovery > Ingresses**.

1.  Click **Create.**

1.  When choosing **Namespace**, ensure it is the same as the one used when you created your deployment. Otherwise, your deployment will not be available when you attempt to select **Target Service**, as in Step 8 below.

1.  Enter a **Name**, such as **hello**.

1.  Specify your **Path**, such as `/hello`.

1.  In the **Target Service** field, drop down the list and choose the name that you set for your service.

1.  In the **Port** field, drop down the list and select `80`.

1.  Click **Create** at the bottom right.

**Result:** The application is assigned a `sslip.io` address and exposed. It may take a minute or two to populate.


### View Your Application

From the **Deployments** page, find the **Endpoints** column for your deployment and click on an endpoint. The endpoints available will depend on how you configured the port you added to your deployment. For endpoints where you do not see a randomly assigned port, append the path you specified when creating the ingress to the IP address. For example, if your endpoint looks like `xxx.xxx.xxx.xxx` or `https://xxx.xxx.xxx.xxx` change it to `xxx.xxx.xxx.xxx/hello` or `https://xxx.xxx.xxx.xxx/hello`.

Your application will open in a separate window.

#### Finished

Congratulations! You have successfully deployed a workload exposed via an ingress.

#### What's Next?

When you're done using your sandbox, destroy the Rancher Server and your cluster. See one of the following:

- [Amazon AWS: Destroying the Environment](../deploy-rancher-manager/aws.md#destroying-the-environment)
- [DigitalOcean: Destroying the Environment](../deploy-rancher-manager/digitalocean.md#destroying-the-environment)
- [Vagrant: Destroying the Environment](../deploy-rancher-manager/vagrant.md#destroying-the-environment)
