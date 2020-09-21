Überprüfe mit `minikube version`{{execute}} die Minikube Version. (_Dieser Schritt ist optional_)

Starte mit `minikube start`{{execute}} den Minikube Kubernetes Cluster.
Bitte beachte, dass es eine Weile dauert bis dieser Cluster hochgefahren ist.

Mit `minikube status`{{execute}} überprüfst du den Status des Clusters. Wenn er erfolgreich hochgefahren ist,
liefert dieser Befehl:

```
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Running
```