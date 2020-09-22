Was passiert, wenn ein Container über das Limit Speicher anfordert? Wir simulieren
dies mit einem weiteren Pod `cat memory-demo-pod-2.yaml | yq r -C -`{{execute}} indem
der `stress` Befehl weiterhin 150 MB RAM Speicher anfordert, das Limit aber auf 100 MB
reduziert wurde.

