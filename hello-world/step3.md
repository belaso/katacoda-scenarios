Der Speicherverbrauch eines Containers innerhalb eines Pods kann mit
dem Befehl `kubectl top` untersucht werden.
Siehe auch https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#top.

Um `kubectl top` verwenden zu können, muss zuerst in Minikube der Metrics Server AddOn
installiert werden. Bitte führe `minikube addons enable metrics-server`{{execute}} aus.

