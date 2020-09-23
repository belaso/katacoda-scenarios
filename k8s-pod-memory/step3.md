Der Speicherverbrauch eines Containers innerhalb eines Pods kann mit
dem Befehl `kubectl top` untersucht werden.
Siehe auch https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#top.

## Metrics Server AddOn

Um `kubectl top` verwenden zu können, muss aber zuerst in Minikube der Metrics Server AddOn
installiert werden. Bitte führe `minikube addons enable metrics-server`{{execute}} aus.
Beachte bitte, dass es 2 bis 3 Minuten dauern kann bis der Metrics Server funktionsfähig ist.

## kubectl top

Mit dem Befehl `kubectl top pod memory-demo-pod --containers`{{execute}} kannst du den aktuellen
Speicherverbrauch des Pods `memory-demo-pod` abfragen.

Wenn du den `kubectl top ...` Befehl **zu früh** ausführst, erhältst du diverse Fehlermeldungen.
In diesem Fall führe den Befehl einfach erneut aus bis er funktioniert, bis also der Metrics Server 
voll funktionsfähig ist.

Nachdem der Metrics Server läuft, liefert der obige `top` Befehl folgende Ausgabe.

```
POD               NAME                    CPU(cores)   MEMORY(bytes)
memory-demo-pod   memory-demo-container   57m          150Mi
```

Erwartungsgemäß verbraucht der `memory-demo-container` Container 150 MB und das liegt unterhalb des 
eingegebenen Limits von 200 MB.

## Fazit

Fordert ein Container RAM Speicher unterhalb des maximalen Limits, so wird diese Anforderung von Kubernetes bedient.
Die Angabe einers regulären Wertes für den Speicherverbrauch hilft Kubernetes die Pods effizient
auf unterschiedlichen Nodes zu verteilen.

Fordert ein Container mehr RAM Speicher als das maximale Limit, so wird der Container mit einem Out of Memory Fehler beendet.
Dies wird im nächsten Abschnitt untersucht.
