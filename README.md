# Gestion multitenant avec RBAC dans Openshift


### Déploiement 

Pour déployer les ressources de demo multitenant RBAC, il suffit d'appliquer les fichiers subscription et channel sur un cluster ayant Advanced Cluster Management d'installé. 

``` 
oc apply -f subscription.yaml
oc apply -f channel.yaml
```

Appliquer ensuite le label integrations-rbac=yes sur le ou les clusters souhaités. 

### Définition des groupes

#### groupe: demo-rbac-developpeurs

Accès complet au projet integrations-dev
Accès limité au projet integrations-preprod
Aucun accès au projet integrations-prod

#### groupe: demo-rbac-operations

Accès limité au projet integrations-dev
Accès limité au projet integrations-preprod
Accès limité au projet integrations-prod

#### groupe: demo-rbac-tests

Aucun accès au projet integrations-dev
Accès limité au projet integrations-preprod
Aucun accès au projet integrations-prod

### Définition des usagers

* Les usagers ont préalablement été créé dans Red Hat SSO 

- demo-rbac-dev membre du groupe demo-rbac-developpeurs
- demo-rbac-ops membre du groupe demo-rbac-operations
- demo-rbac-tst membre du groupe demo-rbac-testeurs

### Définition des roles 

demo-rbac-developpeurs-access-to-dev
| Ressource                   | Accès |
| --------------------------- | ----- |
| Projet integrations-dev     | Full  |

demo-rbac-developpeurs-access-to-preprod
| Ressource                       | Accès |
| ------------------------------- | ----- |
| Projet integrations-preprod     | Lire  |

demo-rbac-operations-access-to-dev
| Ressource                   | Accès |
| --------------------------- | ----- |
| Projet integrations-dev     | Lire  |

demo-rbac-operations-access-to-preprod
| Ressource                       | Accès |
| ------------------------------- | ----- |
| Projet integrations-preprod     | Lire  |

demo-rbac-operations-access-to-prod
| Ressource                    | Accès   |
| ---------------------------- | ------- |
| Projet integrations-prod     | Limité  |
| Secrets                      | List    |

demo-rbac-testeurs-access-to-preprod
| Ressource                       | Accès |
| ------------------------------- | ----- |
| Projet integrations-preprod     | Full  |

### Demo script


   