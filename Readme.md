# Descrição

    Projeto para teste de Kubernates, com services, pods e configmap
![Arquitetura do Projeto](images/arquitetura.jpeg)
    
# Requisitos:
    Instalar kubectl
    Instalar oracleVM
    Instalar MiniKUbe -> para criar o clusters, precisa ser linkado com o drive de virtualização no caso oracleVM

# Conceitos:

    Pod = Casulo 1 ou mais containers, 1 endereço de IP, efêmero -> Pod of whales
    Service = Tipo um sidecar do Pod, dando mais poderes ao mesmo.
    ConfigMap = Variaveis (Chave/valor)
    ReplicaSet = Tem a capacidade de encapsular 1 ou + Pods -> Controla os Pods(Quantidade de replicas no ar)
    https://kubernetes.io/docs/concepts/workloads/pods/
    Deployments = Encapsula o ReplicaSet e Pods num unico arquivo e ainda faz o controle de versionamento

# Principais comandos:


## Rodar Aplicação
    minikube start driver=virtalbox
    kubectl apply -f portal-noticias.yaml
    kubectl apply -f sistema-noticias.yaml 
    kubectl apply -f svc-sistema-noticias.yaml 
    kubectl apply -f svc-portal-noticias.yaml
    e assim por diante em todos os arquivos *.yaml
    
    Frontend:
    http://"node-ip":30000
    
    Backoffice:
    http://192.168.99.100:30001/
    user: admin
    password: admin

## MiniKube:
    minikube start driver=virtalbox
    minikube ssh

## Visualizar nodes:
    kubectl get nodes -o wide

## Pods:
    kubectl get pods -o wide
    kubectl describe pod "name"
    kubectl delete pod "name"
    kubectl exec -it pod-1 -- bash
    kubectl exec -it pod-1 --container "nome_do_container" -- bash #Acessar um pod que tenha mais de um container
    kubectl delete pods -- all

## Service:
    kubectl get svc
    kubectl get services
    kubectl delete svc -- all

## ConfigMap:
    kubectl get configmap
    kubectl describe configmap "name"

## Deployment
    kubectl rollout history  deployment portal-noticias-deployment # Listar historico de versionamento de um deployment
    kubectl get deployments
    kubectl annotate  deployment portal-noticias-deployment kubernates.io/change-cause="Criando deployment 1.0" --overwrite # Alterar a mensagem do commit







