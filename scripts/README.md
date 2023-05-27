# Extending kubectl - kubeplugin script

## Useful material

Install and Set Up kubectl on Linux https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

WSL+Docker: Kubernetes on the Windows Desktop https://kubernetes.io/blog/2020/05/21/wsl-docker-kubernetes-on-the-windows-desktop/

Extend kubectl with plugins https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/

Kubectl plugins available https://krew.sigs.k8s.io/plugins/


## Plugin usage

      curl -O https://raw.githubusercontent.com/EvgenPavlyuchek/AsciiArtify/main/scripts/kubeplugin
      chmod +x kubeplugin
      ./kubeplugin [<resource_type>] [<namespace>]
      or
      sudo cp kubeplugin /usr/local/bin/kubectl-kubeplugin
      kubectl plugin list
      kubectl kubeplugin [<resource_type>] [<namespace>]

## Example of use

    kubectl kubeplugin pods argocd

    pods, argocd, argocd-application-controller-0, 1m, 35Mi
    pods, argocd, argocd-applicationset-controller-7c9cb6785d-lfs5t, 1m, 35Mi
    pods, argocd, argocd-dex-server-69dbdcbf7d-q4l59, 1m, 33Mi
    pods, argocd, argocd-notifications-controller-f9d4457df-8sltz, 1m, 29Mi
    pods, argocd, argocd-redis-74cb89f466-vhh4z, 1m, 8Mi
    pods, argocd, argocd-repo-server-677867cd57-8gwp8, 1m, 39Mi
    pods, argocd, argocd-server-74cd6d578d-b99h2, 1m, 38Mi


