## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.2.7 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | = 4.47.0 |
| <a name="requirement_helm"></a> [helm](#requirement\_helm) | >= 2.6.0 |
| <a name="requirement_kubectl"></a> [kubectl](#requirement\_kubectl) | >= 1.14 |
| <a name="requirement_kubernetes"></a> [kubernetes](#requirement\_kubernetes) | >= 2.13.1 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 4.47.0 |
| <a name="provider_aws.virginia"></a> [aws.virginia](#provider\_aws.virginia) | 4.47.0 |
| <a name="provider_kubectl"></a> [kubectl](#provider\_kubectl) | 1.14.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_eks_blueprints"></a> [eks\_blueprints](#module\_eks\_blueprints) | github.com/aws-ia/terraform-aws-eks-blueprints | v4.28.0 |
| <a name="module_eks_blueprints_kubernetes_addons"></a> [eks\_blueprints\_kubernetes\_addons](#module\_eks\_blueprints\_kubernetes\_addons) | github.com/aws-ia/terraform-aws-eks-blueprints//modules/kubernetes-addons | v4.28.0 |
| <a name="module_eks_blueprints_outputs"></a> [eks\_blueprints\_outputs](#module\_eks\_blueprints\_outputs) | ../../../iaac/terraform/utils/blueprints-extended-outputs | n/a |
| <a name="module_karpenter"></a> [karpenter](#module\_karpenter) | terraform-aws-modules/eks/aws//modules/karpenter | ~> 19.12 |
| <a name="module_kubeflow_components"></a> [kubeflow\_components](#module\_kubeflow\_components) | ./vanilla-components/ | n/a |
| <a name="module_vpc"></a> [vpc](#module\_vpc) | terraform-aws-modules/vpc/aws | 3.14.4 |

## Resources

| Name | Type |
|------|------|
| [kubectl_manifest.karpenter_node_template_cpu](https://registry.terraform.io/providers/gavinbunney/kubectl/latest/docs/resources/manifest) | resource |
| [kubectl_manifest.karpenter_node_template_gpu](https://registry.terraform.io/providers/gavinbunney/kubectl/latest/docs/resources/manifest) | resource |
| [kubectl_manifest.karpenter_provisioner](https://registry.terraform.io/providers/gavinbunney/kubectl/latest/docs/resources/manifest) | resource |
| [kubectl_manifest.karpenter_provisioner_gpu](https://registry.terraform.io/providers/gavinbunney/kubectl/latest/docs/resources/manifest) | resource |
| [aws_ec2_instance_type_offerings.availability_zones_cpu](https://registry.terraform.io/providers/hashicorp/aws/4.47.0/docs/data-sources/ec2_instance_type_offerings) | data source |
| [aws_ec2_instance_type_offerings.availability_zones_gpu](https://registry.terraform.io/providers/hashicorp/aws/4.47.0/docs/data-sources/ec2_instance_type_offerings) | data source |
| [aws_ecrpublic_authorization_token.token](https://registry.terraform.io/providers/hashicorp/aws/4.47.0/docs/data-sources/ecrpublic_authorization_token) | data source |
| [aws_eks_cluster_auth.this](https://registry.terraform.io/providers/hashicorp/aws/4.47.0/docs/data-sources/eks_cluster_auth) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_cluster_name"></a> [cluster\_name](#input\_cluster\_name) | Name of cluster | `string` | n/a | yes |
| <a name="input_cluster_region"></a> [cluster\_region](#input\_cluster\_region) | Region to create the cluster | `string` | n/a | yes |
| <a name="input_eks_version"></a> [eks\_version](#input\_eks\_version) | The EKS version to use | `string` | `"1.25"` | no |
| <a name="input_enable_aws_telemetry"></a> [enable\_aws\_telemetry](#input\_enable\_aws\_telemetry) | Enable AWS telemetry component | `bool` | `true` | no |
| <a name="input_kf_helm_repo_path"></a> [kf\_helm\_repo\_path](#input\_kf\_helm\_repo\_path) | Full path to the location of the helm repo for KF | `string` | `"./kubeflow-manifests"` | no |
| <a name="input_node_instance_type"></a> [node\_instance\_type](#input\_node\_instance\_type) | The instance type of an EKS node | `string` | `"m5.16xlarge"` | no |
| <a name="input_node_instance_type_gpu"></a> [node\_instance\_type\_gpu](#input\_node\_instance\_type\_gpu) | The instance type of a gpu EKS node. Will result in the creation of a separate gpu node group when not null | `string` | `"g4dn.xlarge"` | no |
| <a name="input_notebook_cull_idle_time"></a> [notebook\_cull\_idle\_time](#input\_notebook\_cull\_idle\_time) | If a Notebook's LAST\_ACTIVITY\_ANNOTATION from the current timestamp exceeds this value then the Notebook will be scaled to zero (culled). ENABLE\_CULLING must be set to 'true' for this setting to take effect.(minutes) | `string` | `30` | no |
| <a name="input_notebook_enable_culling"></a> [notebook\_enable\_culling](#input\_notebook\_enable\_culling) | Enable Notebook culling feature. If set to true then the Notebook Controller will scale all Notebooks with Last activity older than the notebook\_cull\_idle\_time to zero | `string` | `false` | no |
| <a name="input_notebook_idleness_check_period"></a> [notebook\_idleness\_check\_period](#input\_notebook\_idleness\_check\_period) | How frequently the controller should poll each Notebook to update its LAST\_ACTIVITY\_ANNOTATION (minutes) | `string` | `5` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_configure_kubectl"></a> [configure\_kubectl](#output\_configure\_kubectl) | Configure kubectl: make sure you're logged in with the correct AWS profile and run the following command to update your kubeconfig |
| <a name="output_eks_cluster_id"></a> [eks\_cluster\_id](#output\_eks\_cluster\_id) | EKS cluster ID |
| <a name="output_eks_managed_nodegroup_arns"></a> [eks\_managed\_nodegroup\_arns](#output\_eks\_managed\_nodegroup\_arns) | EKS managed node group arns |
| <a name="output_eks_managed_nodegroup_ids"></a> [eks\_managed\_nodegroup\_ids](#output\_eks\_managed\_nodegroup\_ids) | EKS managed node group ids |
| <a name="output_eks_managed_nodegroup_role_name"></a> [eks\_managed\_nodegroup\_role\_name](#output\_eks\_managed\_nodegroup\_role\_name) | EKS managed node group role name |
| <a name="output_eks_managed_nodegroup_status"></a> [eks\_managed\_nodegroup\_status](#output\_eks\_managed\_nodegroup\_status) | EKS managed node group status |
| <a name="output_eks_managed_nodegroups"></a> [eks\_managed\_nodegroups](#output\_eks\_managed\_nodegroups) | EKS managed node groups |
| <a name="output_region"></a> [region](#output\_region) | AWS region |
| <a name="output_vpc_cidr"></a> [vpc\_cidr](#output\_vpc\_cidr) | VPC CIDR |
| <a name="output_vpc_private_subnet_cidr"></a> [vpc\_private\_subnet\_cidr](#output\_vpc\_private\_subnet\_cidr) | VPC private subnet CIDR |
| <a name="output_vpc_public_subnet_cidr"></a> [vpc\_public\_subnet\_cidr](#output\_vpc\_public\_subnet\_cidr) | VPC public subnet CIDR |
