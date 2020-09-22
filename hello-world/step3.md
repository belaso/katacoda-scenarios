Der Speicherverbrauch eines Containers innerhalb eines Pods kann mit
dem Befehl `kubectl top` untersucht werden.
Siehe auch https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#top.

Um `kubectl top` verwenden zu können, muss aber zuerst in Minikube der Metrics Server AddOn
installiert werden. Bitte führe `minikube addons enable metrics-server`{{execute}} aus.
Beachte bitte, dass es 2-3 Minuten dauern kann bis der Metrics Server funktionsfähig ist.

Mit dem Befehl `kubectl top pod memory-demo-pod`{{execute}} kannst du dann den aktuellen
Speicherverbrauch des Pods `memory-demo-pod` abfragen.

Wenn du den `kubectl top ...` Befehl **zu früh** ausführst, erhältst du Fehlermeldungen wie: 
```
Error from server (NotFound): the server could not find the requested resource (get services http:heapster:)
```
und
```
Error from server (NotFound): podmetrics.metrics.k8s.io "default/memory-demo-pod" not found
```
In diesem Fall führe Befehl einfach erneut aus.

Nachdem der Metrics Server läuft, liefert der obige `top` Befehl folgende Ausgabe.
```
NAME              CPU(cores)   MEMORY(bytes)
memory-demo-pod   64m          150Mi  
```

Mit dem zusätzlichen `--containers` Parameter 
`kubectl top pod memory-demo-pod --containers`{{execute}}
erhältst du den Speichervertrauch des Pods nach Container ausgeschlüsselt.
```
POD               NAME                    CPU(cores)   MEMORY(bytes)
memory-demo-pod   memory-demo-container   57m          150Mi
```

Erwartungsgemäß verbraucht der `memory-demo-container` Container 150 MB und das liegt unterhalb des 
eingegebenen Limits von 200 MB.