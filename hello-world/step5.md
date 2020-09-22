Ein Pod kann mehr als ein Container enthalten. Wir simulieren nun den Fall,
dass lediglich ein Container mehr Speicher anfordert als erlaubt
`cat memory-demo-pod-3.yaml | yq r -C -`{{execute}}.

Deploye den `memory-demo-pod-3` Pod mit dem Befehl 
`kubectl apply -f memory-demo-pod-3.yaml`{{execute}}.

Untersuche nun den Status des Pods `memory-demo-pod-3` mit dem Befehl
`kubectl get pod  memory-demo-pod-3`{{execute}}.
