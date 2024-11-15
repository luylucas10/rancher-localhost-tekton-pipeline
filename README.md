# Tekton Pipeline for .NET Core Applications

This repository contains Tekton pipelines for building, testing, and deploying .NET Core applications. The pipelines are designed to work with GitLab, ArgoCD, SonarQube and Harbor.

## Repository Structure

```plaintext
[Chart.yaml](http://_vscodecontentref_/1)
LICENSE
[README.md](http://_vscodecontentref_/2)
templates/
  container-pipeline/
    [container-pipeline-event-listener.yaml](http://_vscodecontentref_/3)
    [container-pipeline-ingress.yaml](http://_vscodecontentref_/4)
    [container-pipeline-trigger-binding.yaml](http://_vscodecontentref_/5)
    [container-pipeline-trigger-template.yaml](http://_vscodecontentref_/6)
    [container-pipeline.yaml](http://_vscodecontentref_/7)
  dotnet-pipeline/
    [dotnet-pipeline-event-listener.yaml](http://_vscodecontentref_/8)
    [dotnet-pipeline-ingress.yaml](http://_vscodecontentref_/9)
    [dotnet-pipeline-trigger-binding.yaml](http://_vscodecontentref_/10)
    [dotnet-pipeline-trigger-template.yaml](http://_vscodecontentref_/11)
    [dotnet-pipeline.yaml](http://_vscodecontentref_/12)
    tasks/
      [create-argocd-app.yaml](http://_vscodecontentref_/13)
      [create-app-gitops-config.yaml](http://_vscodecontentref_/14)
      create-image-tag.yaml
      [dotnet-tasks.yaml](http://_vscodecontentref_/15)
      [read-cicd-config.yaml](http://_vscodecontentref_/16)
      [update-app-gitops-config.yaml](http://_vscodecontentref_/17)
  [gitlab-secret.yaml](http://_vscodecontentref_/18)
  [service-account.yaml](http://_vscodecontentref_/19)
[values.yaml](http://_vscodecontentref_/20)
```

### Getting Started

#### Prerequisites

- Kubernetes cluster
- Tekton Pipelines and Tekton Triggers installed
- GitLab, ArgoCD, and SonarQube instances

#### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd <repository-directory>
```

2. Configure the values.yaml file with your specific values:

```yaml
gitlab:
  url: https://gitlab.yourdomain.com
  model:
    repo: https://gitlab.yourdomain.com/path/to/model-helm-chart/repo.git
    namespace: <prefix>
hub:
  url: hub.yourdomain.com
  project: <project>
  tektonImagesProject: tekton
  dockerProxy: docker
argo:
  url: cd.yourdomain.com
sonarqube:
  url: https://sonarqube.yourdomain.com
  token: <token>
  projectKey: <project>
  qualityGateWait: true
```

3. Apply the Kubernetes resources:

```bash
kubectl apply -f templates/service-account.yaml
kubectl apply -f templates/gitlab-secret.yaml
kubectl apply -f templates/dotnet-pipeline/
```

#### Pipelines

##### Container Pipeline

 - Event Listener: container-pipeline-event-listener.yaml
 - Ingress: container-pipeline-ingress.yaml
 - Trigger Binding: container-pipeline-trigger-binding.yaml
 - Trigger Template: container-pipeline-trigger-template.yaml
 - Pipeline: container-pipeline.yaml

##### .NET Pipeline

- Event Listener: dotnet-pipeline-event-listener.yaml
- Ingress: dotnet-pipeline-ingress.yaml
- Trigger Binding: dotnet-pipeline-trigger-binding.yaml
- Trigger Template: dotnet-pipeline-trigger-template.yaml
- Pipeline: dotnet-pipeline.yaml

##### Tasks

- Create ArgoCD App: tasks/create-argocd-app.yaml
- Create App GitOps Config: tasks/create-app-gitops-config.yaml
- Create Image Tag: tasks/create-image-tag.yaml
- .NET Tasks: tasks/dotnet-tasks.yaml
- Read CI/CD Config: tasks/read-cicd-config.yaml
- Update App GitOps Config: tasks/update-app-gitops-config.yaml

License

This project is licensed under the MIT License - see the LICENSE file for details.


This [README.md](http://_vscodecontentref_/21) provides an overview of the repository structure, installation instructions, and details about the pipelines and tasks included in the repository.