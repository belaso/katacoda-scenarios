Der Speicherverbrauch eines Containers innerhalb eines Pods kann mit
dem Befehl `kubectl top` untersucht werden.
Siehe auch https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#top.

Um `kubectl top` verwenden zu können, muss zuerst in Minikube der Metrics Server AddOn
installiert werden. Bitte führe `minikube addons enable metrics-server`{{execute}} aus.
Beachte bitte, dass es 2-3 Minuten dauern kann bis der Metrics Server funktionsfähig ist.

Mit dem Befehl `kubectl top pod memory-demo-pod`{{execute}} kannst du dann den aktuellen
Speicherverbrauch des Pods `memory-demo-pod` abfragen. Mit dem zusätzlichen Parameter 
`kubectl top pod memory-demo-pod --containers`{{execute}} erhältst du den Speichervertrauch
nach Container ausgeschlüsselt. 