Was passiert, wenn ein Container über das Limit Speicher anfordert? Wir simulieren
dies mit einem weiteren Pod `cat memory-demo-pod-2.yaml | yq r -C -`{{execute}}.

Der `stress` Befehl fordert weiterhin 150 MB RAM Speicher,
das maximale Limit wurde aber auf 100 MB reduziert.

## Fehlerhafter Pod

Deploye den `memory-demo-pod-2` Pod mit dem Befehl 
`kubectl apply -f memory-demo-pod-2.yaml`{{execute}}.

Der `stress` Befehl fordert 150 MB Speicher, obwohl lediglich 100 MB maximal erlaubt sind.

Betrachte nun den Status des Pods mit `kubectl get pod  memory-demo-pod-2`{{execute}} und
du erhältst folgende Ausgabe

```
NAME                READY   STATUS      RESTARTS   AGE
memory-demo-pod-2   0/1     OOMKilled   1          1m
```

Der `Status` des Pods ist `OOMKilled`. `OOM` steht hier für _Out of Memory_.
Der Container `memory-demo-container-2` fordert mehr Speicher an als erlaubt 
und wird deshalb von Kubernetes beendet.

## Fazit

Gib innerhalb einer Pod Definition immer sowohl den regulären als auch den maximalen
Speicherverbrauch an.

Mit der Angabe des regulären Speicherverbrauchs hilftst du Kubernetes die Pods
effizient auf die Nodes zu verteilen. Mit der Angabe des maximalen Speicherverbrauchs
hilftst du Kubernetes Pods bzw. Container zu erkennen, die zu viel Speicher anfordern.
Kubernetes kann dann diese Pods beenden bzw. automatisch erneut starten.
 