Du deployst jetzt einen einfachen Pod und gibst an wieviel RAM Speicher
der Pod erhalten soll. Die Definition des Pods 
findest du hier: `cat memory-demo-pod.yaml | yq r -C -`{{execute}}.

Die RAM Speicher Anforderungen sind dem Abschnitt
<pre>
	resources:
      limits:
        memory: "200Mi"
      requests:
        memory: "100Mi"
</pre>
definiert.

Die obigen Einträge bedeuten, dass der Docker Container innerhalb des Pods
- maximal 200 MB RAM erhalten darf und
- 100 MB RAM für den normalen Betrieb erhält

Deploye  den Pod nun mit dem Befehl `kubectl apply -f memory-demo-pod.yaml`{{execute}}.

Mit `kubectl get pod memory-demo-pod`{{execute}} kannst du überprüfen, ob dein Pod
läuft. Der `STATUS` des Pods ist dann `Running`.

Innerhalb des Pods wurde der Docker Container https://hub.docker.com/r/polinux/stress 
gestartet. Beim Starten des Containers wird der `stress` Befehl ausgeführt, 
der 150 MB Speicher anfordert. Also mehr als der initiale Request von 100 MB 
aber weniger als das Limit von 200 MB.

Den Befehl 'stress' verwenden wir um auf einfache Weise unterschiedliche Verhaltensweisen
von Anwendungen zu simulieren. 