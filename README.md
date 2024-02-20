# doit-eks-lens-helm-chart

Repository contains the helm chart templates to install the components required for [EKS Lens](#https://help.doit.com/docs/dashboards/eks-lens).

## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add doit-eks-lens https://doitintl.github.io/doit-eks-lens-helm-chart/

If you had already added this repo earlier, run `helm repo update` to retrieve the latest versions of the packages.You can then run `helm search repo doit-eks-lens` to see the charts.

To generate templates:

    helm template doit-eks-lens-helm-chart/doit-eks-lens

To install the doit-eks-lens chart:

    helm install doit-eks-lens doit-eks-lens-helm-chart/doit-eks-lens --set region=<EKS-CLUSTER-REGION> \
        --set metricsDeploymentId=<DEPLOYMENT-ID> \
        --set s3_bucket=<S3-BUCKET-NAME> \
        --set s3_prefix=<S3-BUCKET-PREFIX> \
        --set role_arn=<IAM-ROLE-ARN> \
        --namespace doit-eks-metrics \
        --create-namespace

Example:

    helm install doit-eks-lens doit-eks-lens-helm-chart/doit-eks-lens --set region=us-east-1 \
        --set metricsDeploymentId=2Dw7oXwSkgjwjsXGcSMr \
        --set s3_bucket=doitintl-eks-metrics-410386763839-us-east-1 \
        --set s3_prefix=eks-metrics/410386763839/us-east-1/public \
        --set role_arn=arn:aws:iam::410386763839:role/doit_eks_us-east-1_public \
        --namespace doit-eks-metrics \
        --create-namespace

To uninstall the chart:

    helm delete doit-eks-lens --namespace doit-eks-metrics 