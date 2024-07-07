# Helm Limitations
1. Due to current format of using helm charts (Single template) & multiple applications.
   * Below tpl function `.Files.Get` (To read file content) written to parse individual app content.
   ```yaml
   {{- $configmapPath := printf "../apps/%s/configmap.yaml" .Values.appNameGeneric }}
   {{- printf "Debug: File Path - %s" $configmapPath | nindent 2 }}
   {{- printf "Debug: File Content - %s" (.Files.Get $configmapPath) | nindent 2 }}
   ```
   * Output:
  ```yaml
  apiVersion: v1
  kind: ConfigMap
  metadata:
    name: app-01-configmap
    namespace: stg
    labels:
      app: app-01
  data:
    Debug: File Path - ../apps/app-01/configmap.yaml
    Debug: File Content -
  ```
   
3. Helm Limitation to execute tpl function
4. **`Solution:`** The issue with the tpl function in Helm not reading the file content from a path outside the chart directory is due to the way Helm handles file references. Helm can only reference files that are within the chart directory. To address this limitation, you can use a workaround where you copy the necessary files into the chart directory during the Helm deployment process.
5. With this Solution, to enable Argocd, we need to have templates copied each application directory i.e Duplicate the same template for all applications.  
