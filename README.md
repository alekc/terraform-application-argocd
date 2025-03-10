<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.14.8, < 2.0.0 |
| <a name="requirement_kubectl"></a> [kubectl](#requirement\_kubectl) | ~> 2.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_kubectl"></a> [kubectl](#provider\_kubectl) | ~> 2.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [kubectl_manifest.argo_application](https://registry.terraform.io/providers/alekc/kubectl/latest/docs/resources/manifest) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_additional_sources"></a> [additional\_sources](#input\_additional\_sources) | Additional sources (in yaml manifests) to be applied to the application | `map(string)` | `null` | no |
| <a name="input_additional_yaml_manifests"></a> [additional\_yaml\_manifests](#input\_additional\_yaml\_manifests) | Additional YAML manifests to be applied to the application | `map(string)` | `null` | no |
| <a name="input_annotations"></a> [annotations](#input\_annotations) | Annotations for argocd Application | `map(string)` | `{}` | no |
| <a name="input_app_source"></a> [app\_source](#input\_app\_source) | Type of application source (helm, git) | `string` | `"helm"` | no |
| <a name="input_apply_out_of_sync_only"></a> [apply\_out\_of\_sync\_only](#input\_apply\_out\_of\_sync\_only) | Currently when syncing using auto sync Argo CD applies every object in the application. Turning on selective sync option which will sync only out-of-sync resources. | `bool` | `false` | no |
| <a name="input_argocd_namespace"></a> [argocd\_namespace](#input\_argocd\_namespace) | The name of the target ArgoCD Namespace | `string` | `"argocd"` | no |
| <a name="input_automated_allow_empty"></a> [automated\_allow\_empty](#input\_automated\_allow\_empty) | Allows deleting all application resources during automatic syncing ( false by default ). | `bool` | `false` | no |
| <a name="input_automated_prune"></a> [automated\_prune](#input\_automated\_prune) | Specifies if resources should be pruned during auto-syncing | `bool` | `true` | no |
| <a name="input_automated_self_heal"></a> [automated\_self\_heal](#input\_automated\_self\_heal) | Specifies if partial app sync should be executed when resources are changed only in target Kubernetes cluster and no git change detected | `bool` | `true` | no |
| <a name="input_cascade_delete"></a> [cascade\_delete](#input\_cascade\_delete) | Set to true if this application should cascade delete | `bool` | `true` | no |
| <a name="input_chart"></a> [chart](#input\_chart) | The name of the Helm chart | `string` | `null` | no |
| <a name="input_destination_server"></a> [destination\_server](#input\_destination\_server) | Server specifies the URL of the target cluster and must be set to the Kubernetes control plane API | `string` | `"https://kubernetes.default.svc"` | no |
| <a name="input_destination_server_name"></a> [destination\_server\_name](#input\_destination\_server\_name) | Name is an alternate way of specifying the target cluster by its symbolic name | `string` | `""` | no |
| <a name="input_fail_on_shared_resource"></a> [fail\_on\_shared\_resource](#input\_fail\_on\_shared\_resource) | If true, the Argo CD will fail the sync whenever it finds a resource in the current Application that is already applied in the cluster by another Application. | `bool` | `false` | no |
| <a name="input_helm_api_versions"></a> [helm\_api\_versions](#input\_helm\_api\_versions) | # You can specify the Kubernetes resource API versions to pass to Helm when templating manifests. By default, ArgoCD uses the API versions of the target cluster. The format is [group/]version/kind. | `list(string)` | `null` | no |
| <a name="input_helm_files_parameters"></a> [helm\_files\_parameters](#input\_helm\_files\_parameters) | Use the contents of files as parameters (uses Helm's --set-file) | <pre>list(object({<br>    name : string,<br>    path : bool,<br>  }))</pre> | `null` | no |
| <a name="input_helm_ignore_missing_values"></a> [helm\_ignore\_missing\_values](#input\_helm\_ignore\_missing\_values) | Ignore locally missing valueFiles when installing Helm chart | `bool` | `false` | no |
| <a name="input_helm_kube_version"></a> [helm\_kube\_version](#input\_helm\_kube\_version) | You can specify the Kubernetes API version to pass to Helm when templating manifests. By default, Argo CD uses the Kubernetes version of the target cluster. The value must be semver formatted. Do not prefix with `v`. | `string` | `null` | no |
| <a name="input_helm_namespace"></a> [helm\_namespace](#input\_helm\_namespace) | Optional namespace to template with. If left empty, defaults to the app's destination namespace. | `string` | `null` | no |
| <a name="input_helm_parameters"></a> [helm\_parameters](#input\_helm\_parameters) | Parameters that will override helm\_values | <pre>list(object({<br>    name : string,<br>    value : any,<br>    force_string : bool,<br>  }))</pre> | `null` | no |
| <a name="input_helm_pass_credentials"></a> [helm\_pass\_credentials](#input\_helm\_pass\_credentials) | f true then adds --pass-credentials to Helm commands to pass credentials to all domains | `bool` | `null` | no |
| <a name="input_helm_skip_crd"></a> [helm\_skip\_crd](#input\_helm\_skip\_crd) | If set to true, it will skip the deployment of crd entities from the helm chart | `bool` | `false` | no |
| <a name="input_helm_values"></a> [helm\_values](#input\_helm\_values) | Helm values as a block of yaml | `string` | `null` | no |
| <a name="input_helm_values_files"></a> [helm\_values\_files](#input\_helm\_values\_files) | Helm values files for overriding values in the helm chart. The path is relative to the var.path directory defined above | `list(string)` | `null` | no |
| <a name="input_helm_values_object"></a> [helm\_values\_object](#input\_helm\_values\_object) | Values file as block file. This takes precedence over values | `any` | `null` | no |
| <a name="input_helm_version"></a> [helm\_version](#input\_helm\_version) | Optional Helm version to template with. If omitted it will fall back to look at the 'apiVersion' in Chart.yaml and decide which Helm binary to use automatically. This field can be either 'v2' or 'v3'. | `string` | `null` | no |
| <a name="input_ignore_differences"></a> [ignore\_differences](#input\_ignore\_differences) | Ignore differences at the specified json pointers | `list(any)` | `[]` | no |
| <a name="input_info"></a> [info](#input\_info) | Extra information to show in the Argo CD Application details tab | <pre>list(object({<br>    name : string<br>    value : string<br>  }))</pre> | `null` | no |
| <a name="input_labels"></a> [labels](#input\_labels) | n/a | `map(string)` | `{}` | no |
| <a name="input_managed_namespace_metadata"></a> [managed\_namespace\_metadata](#input\_managed\_namespace\_metadata) | Namespace metadata to be applied to namespaces managed by ArgoCD | <pre>object({<br>    labels : optional(map(string), {})<br>    annotations : optional(map(string), {})<br>  })</pre> | `null` | no |
| <a name="input_name"></a> [name](#input\_name) | The name of this application | `string` | `""` | no |
| <a name="input_namespace"></a> [namespace](#input\_namespace) | n/a | `string` | n/a | yes |
| <a name="input_path"></a> [path](#input\_path) | n/a | `string` | `""` | no |
| <a name="input_project"></a> [project](#input\_project) | The project that this ArgoCD application will be placed into. | `string` | `"default"` | no |
| <a name="input_prune_propagation_policy"></a> [prune\_propagation\_policy](#input\_prune\_propagation\_policy) | Supported policies are background, foreground and orphan. | `string` | `"foreground"` | no |
| <a name="input_release_name"></a> [release\_name](#input\_release\_name) | Release name override (defaults to application name) | `string` | `null` | no |
| <a name="input_replace"></a> [replace](#input\_replace) | If true, the Argo CD will use kubectl replace or kubectl create command to apply changes. | `bool` | `false` | no |
| <a name="input_repo_url"></a> [repo\_url](#input\_repo\_url) | Source of the Helm application manifests | `string` | n/a | yes |
| <a name="input_retry_backoff_duration"></a> [retry\_backoff\_duration](#input\_retry\_backoff\_duration) | The amount to back off. Default unit is seconds, but could also be a duration (e.g. `2m`, `1h`) | `string` | `"5s"` | no |
| <a name="input_retry_backoff_factor"></a> [retry\_backoff\_factor](#input\_retry\_backoff\_factor) | A factor to multiply the base duration after each failed retry | `number` | `2` | no |
| <a name="input_retry_backoff_max_duration"></a> [retry\_backoff\_max\_duration](#input\_retry\_backoff\_max\_duration) | The maximum amount of time allowed for the backoff strategy | `string` | `"3m"` | no |
| <a name="input_retry_limit"></a> [retry\_limit](#input\_retry\_limit) | Number of failed sync attempt retries; unlimited number of attempts if less than 0 | `number` | `5` | no |
| <a name="input_server_side_apply"></a> [server\_side\_apply](#input\_server\_side\_apply) | If true, Argo CD will use kubectl apply --server-side command to apply changes. | `bool` | `false` | no |
| <a name="input_sync_option_create_namespace"></a> [sync\_option\_create\_namespace](#input\_sync\_option\_create\_namespace) | Namespace Auto-Creation ensures that namespace specified as the application destination exists in the destination cluster. | `bool` | `true` | no |
| <a name="input_sync_option_validate"></a> [sync\_option\_validate](#input\_sync\_option\_validate) | disables resource validation (equivalent to 'kubectl apply --validate=true') | `bool` | `false` | no |
| <a name="input_sync_options"></a> [sync\_options](#input\_sync\_options) | A list of sync options to apply to the application | `list(string)` | `[]` | no |
| <a name="input_target_revision"></a> [target\_revision](#input\_target\_revision) | Revision of the Helm application manifests to use | `string` | `""` | no |
| <a name="input_wait_for_deletion"></a> [wait\_for\_deletion](#input\_wait\_for\_deletion) | If set to true, will wait until the object is removed completely from kubernetes before proceeding further | `bool` | `false` | no |
| <a name="input_wait_until_healthy"></a> [wait\_until\_healthy](#input\_wait\_until\_healthy) | If set to true, it will wait until the application has reached status healthy before proceeding further | `bool` | `false` | no |

## Outputs

No outputs.
<!-- END_TF_DOCS -->
