# Helm Example Repository
## 1. helm_repo structure
  * Replicated helm_ngil repo
  * application structure is as bellow
  ````yaml

  ````
## 2. Application files with global, static & overriding values
  * 

## 3. helm upgrade command tested
  * helm command 
  ````yaml
  helm upgrade --install  hello-world chart/ -n stg \
  -f chart/hello-world/values.yaml \
  -f environments/stg-values.yaml \
  -f chart/hello-world/environments/stg-values.yaml \
  --set appNameGeneric=hello-world \
  ````
  * Output
  ````bash
    Release "hello-world" has been upgraded. Happy Helming!
    NAME: hello-world
    LAST DEPLOYED: Fri Jul  5 07:49:57 2024
    NAMESPACE: stg
    STATUS: deployed
    REVISION: 4
    TEST SUITE: None
  ````
## 4. create helm repo & push to registry

## 5. Test helm package 

Add this repository to Helm.

```
helm repo add examples https://helm.github.io/examples
```

Install an example.

```
helm install ahoy examples/hello-world
```
