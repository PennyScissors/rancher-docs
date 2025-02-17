---
title: Adding a Pod Security Policy
---

<head>
  <link rel="canonical" href="https://ranchermanager.docs.rancher.com/how-to-guides/new-user-guides/manage-clusters/add-a-pod-security-policy"/>
</head>

:::note Prerequisite:

The options below are available only for clusters that are [launched using RKE.](../../../pages-for-subheaders/launch-kubernetes-with-rancher.md)

:::

When your cluster is running pods with security-sensitive configurations, assign it a [pod security policy](../authentication-permissions-and-global-configuration/create-pod-security-policies.md), which is a set of rules that monitors the conditions and settings in your pods. If a pod doesn't meet the rules specified in your policy, the policy stops it from running.

You can assign a pod security policy when you provision a cluster. However, if you need to relax or restrict security for your pods later, you can update the policy while editing your cluster.

1. Click **☰ > Cluster Management**.
1. Go to the cluster to which you want to apply a pod security policy and click **⋮ > Edit Config**.
1. From **Pod Security Policy Support**, select **Enabled**.

    :::note

    This option is only available for clusters [provisioned by RKE](../../../pages-for-subheaders/launch-kubernetes-with-rancher.md).

    :::

4. From the **Default Pod Security Policy** drop-down, select the policy you want to apply to the cluster.

    Rancher ships with [policies](../authentication-permissions-and-global-configuration/create-pod-security-policies.md#default-psps) of `restricted` and `unrestricted`, although you can [create custom policies](../authentication-permissions-and-global-configuration/create-pod-security-policies.md#creating-psps) as well.

5. Click **Save**.

**Result:** The pod security policy is applied to the cluster and any projects within the cluster.

:::note

Workloads already running before assignment of a pod security policy are grandfathered in. Even if they don't meet your pod security policy, workloads running before assignment of the policy continue to run.

To check if a running workload passes your pod security policy, clone or upgrade it.

:::