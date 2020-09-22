Der Speicherverbrauch eines Containers innerhalb eines Pods kann mit
dem Befehl `kubectl top` untersucht werden.
Siehe auch https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#top.

Um `kubectl top` verwenden zu können, muss zuerst in Minikube der Metrics Server AddOn
installiert werden. Bitte führe `minikube addons enable metrics-server`{{execute}} aus.
Beachte bitte, dass es 2-3 Minuten dauern kann bis der Metrics Server funktionsfähig ist.

Mit dem Befehl `kubectl top pod memory-demo-pod`{{execute}} kannst du dann den aktuellen
Speicherverbrauch des Pods `memory-demo-pod` abfragen.

Wenn du den `top` Befehl zu früh ausführst, erhältst du 
```
Error from server (NotFound): the server could not find the requested resource (get services http:heapster:)
```
und danach 
```
Error from server (NotFound): podmetrics.metrics.k8s.io "default/memory-demo-pod" not found
```
als Fehlermeldung. In diesem Fall führe den obigen `top` Befehl einfach erneut aus.

Nachdem der Metrics Server läuft, liefert der obige `top` Befehl folgende Ausgabe
```
NAME              CPU(cores)   MEMORY(bytes)
memory-demo-pod   64m          150Mi  
```

Mit dem zusätzlichen Parameter 
`kubectl top pod memory-demo-pod --containers`{{execute}}
erhältst du den Speichervertrauch des Pods nach Container ausgeschlüsselt. 