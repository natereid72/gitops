# Testing Crossplane with Argo CD

This repo will configure Argo CD to install Crossplane and Gatekeeper into the cluster Argo CD is running in. Secondly, it installs a Crossplane configuration for Azure Cloud that defines XRDs and Composition to deploy an AKS cluster. It then makes an Azure Cloud config (`aks-cluster`) available for creation of the AKS cluster.

For MacOS only, you can use the shell script file located [here](https://github.com/natereid72/cp-k8sScripts/blob/main/argo-cp-all-in-one.sh) to automate the process.

/platform contains the XRD, Composition, and Provider configs.

/aks contains an example XR manifest to create an AKS cluster

  * You can configure the Argo CD aks-cluster Applicaiton to use aks/xrc or aks/xr to see the difference between starting with an XRC or XR (default aks/xr)

/policy contains a simple example Gatekeeper config.

In a production model, these three directories would reside in separate repositories.

/argoapps contains application deifnitions for argoCD to install Crossplane UXP and Gatekeepr, with additional apps that consume the platform, aks, amd policy directories.

[Blog post that provides some background on this repo](https://vrelevant.net/crossplane-and-gitops-lets-get-to-the-good-stuff/)

[Additional post that delves into the XRC vs. XR topic in more detail](https://vrelevant.net/crossplane-with-argo-cd-xrc-or-xr/)

_Prior to using this repository, you will need a K8s cluster with Crossplane and Argo CD installed. You will also need to create a ProviderConfig and a secret for the provider to authenticate to your Azure tenant. Directions for all of this are available at Argo CD and Upbound docs. For a fully relaized GitOps model, we could add something like SealedSecrets to also inlcude the ProviderConfig and Secret within the repo. For directions on installing Crossplane and configuring the Azure Provider, see [here](https://crossplane.io/docs/latest/reference/install.html#install-crossplane) and [here](https://crossplane.io/docs/latest/cloud-providers/azure/azure-provider.html). For directions of installing Argo CD, see [here](https://argo-cd.readthedocs.io/en/stable/getting_started/). Altrnatively, if you are on MacOS you can use the shell scripts located [here](https://github.com/natereid72/cp-k8sScripts) to install Crossplane and Argo CD preconfigured for this repo._

