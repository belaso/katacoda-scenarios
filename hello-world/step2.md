Schaue dir `cat memory-demo-pod.yaml`{{execute}} an. Diesen Pod werden wir gleich in dem
neu erzeugten Cluster deployen.

Der RAM Speicher wird dem Pod / Container in dem Abschnitt
```
	resources:
      limits:
        memory: "200Mi"
      requests:
        memory: "100Mi"
```
zugewiesen. Die obigen Einträge bedeuten, dass der Pod / Container
- 100 MB Memory für den normalen Betrieb benötigt `requests`
- 200 MB die obere Grenze ist, die der Pod verwenden darf

