
# Automatically Deploying Application to Kubernetes with ArgoCD

## Installation k3d and ArgoCD

Repeat steps from the previous DOC file https://github.com/EvgenPavlyuchek/AsciiArtify/blob/main/doc/POC.md

## Deploying Application with ArgoCD

Creating App Via ArgoCD UI with the following repo https://github.com/EvgenPavlyuchek/go-demo-app

![Image](argo03.png)
![Image](argo04.png)

## Tune app in order to check Syncing via UI

![Image](argo05.png)

## Checking the application using CLI

    kubectl port-forward svc/ambassador -n demo 8088:80
    wget -O /tmp/g.png https://www.pngmart.com/files/12/Funny-Kolobanga-PNG-Background-Image.png
    curl -F 'image=@/tmp/g.png' localhost:8088/img/

![Image](demo2.gif)

Demo link: https://asciinema.org/a/587761