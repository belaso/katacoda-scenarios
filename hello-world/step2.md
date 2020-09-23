Du deployst jetzt einen einfachen Pod und gibst an wieviel RAM Speicher
der Docker Container innerhalb des Pods maximal (200 MB) und regulär (100 MB) erhalten soll.

Die Definition des Pods findest du hier `cat memory-demo-pod.yaml | yq r -C -`{{execute}}.

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

## Stress

Innerhalb des Pods wird der Docker Container https://hub.docker.com/r/polinux/stress 
gestartet. Nach dem Start des Containers wird der `stress` Befehl ausgeführt, 
der 150 MB RAM Speicher anfordert. Also mehr als die 100 MB, die für den Container vorgesehen sind 
aber weniger als das maximale Limit von 200 MB.

Den Befehl 'stress' simuliert hier eine Anwendung, die einen 150 MB RAM Speicher benötigt. 

## Deployment

Deploye den Pod nun mit dem Befehl `kubectl apply -f memory-demo-pod.yaml`{{execute}}.

Mit `kubectl get pod memory-demo-pod`{{execute}} kannst du überprüfen, dass dein Pod
läuft. Der `STATUS` des Pods ist dann `Running`.