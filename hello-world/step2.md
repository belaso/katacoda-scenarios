Schaue dir die Definition des Pods mit `cat memory-demo-pod.yaml | yq r -C -`{{execute}} an.
Diesen Pod werden wir gleich in dem vorhin erzeugten Cluster deployen.

Die RAM Speicher Anforderungen sind dem Abschnitt
```
	resources:
      limits:
        memory: "200Mi"
      requests:
        memory: "100Mi"
```
definiert.

Die obigen Einträge bedeuten:
- maximal 200 MB RAM darf der Container anfordern und
- 100 MB RAM ist für den normalen Betrieb notwendig

Deploye  den Pod nun mit dem Befehl `kubectl apply -f memory-demo-pod`{{execute}}.

Mit `kubectl get pod memory-demo-pod`{{execute}} kannst du überprüfen, ob dein Pod
läuft. Der `STATUS` des Pods ist dann `Running`.

Innerhalb des Pods wurde der Docker Container https://hub.docker.com/r/polinux/stress 
gestartet. Beim Starten des Containers wird der `stress` Befehl ausgeführt, 
der 150 MB Speicher anfordert. Also mehr als der initiale Request von 100 MB 
aber weniger als das Limit von 200 MB.