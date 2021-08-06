# Gestion multitenant avec RBAC dans Openshift


### Déploiement 

Pour déployer les ressources de demo multitenant RBAC, il suffit d'appliquer les fichiers subscription et channel sur un cluster ayant Advanced Cluster Management d'installé. 

``` 
oc apply -f subscription.yaml
oc apply -f channel.yaml
```

Appliquer ensuite le label multitenant-rbac=yes sur le ou les clusters souhaités. 

### Définition des roles

#### groupe: demo-rbac-developpeurs

Accès complet au projet multitenant-rbac-dev
Accès limité au projet multitenant-rbac-preprod
Aucun accès au projet multitenant-rbac-prod

#### groupe: demo-rbac-operations

Accès limité au projet multitenant-rbac-dev
Accès limité au projet multitenant-rbac-preprod
Accès limité au projet multitenant-rbac-prod

#### groupe: demo-rbac-tests

Aucun accès au projet multitenant-rbac-dev
Accès limité au projet multitenant-rbac-preprod
Aucun accès au projet multitenant-rbac-prod

### Définition des usagers

* Les usagers ont préalablement été créé dans Red Hat SSO 

demo-rbac-dev membre du groupe demo-rbac-developpeurs
demo-rbac-ops membre du groupe demo-rbac-operations
demo-rbac-tst membre du groupe demo-rbac-preprod

### Demo script

