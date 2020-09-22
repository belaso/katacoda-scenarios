Schaue dir `cat memory-demo-pod.yaml`{{execute}} an. Diesen Pod werden wir gleich in dem
neu erzeugten Cluster deployen.

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

Mit `kubectl get pod memory-demo-pod` kannst du überprüfen, ob dein Pod
läuft. Der `STATUS` des Pods ist dann `Running`.