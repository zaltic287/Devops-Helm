# HELM : PREMIER UPGRADE


<br>

3 méthodes pour déployer des charts :

		* la CLI (à éviter à tout prix)

		* le values.yaml (c'est mieux ;) )

		* les HelmReleases (ah ça c'est bien)

<br>


```
helm install mywp --values values.yaml bitnami/wordpress
helm get <elements> <mywp>
```

---------------------------------------------------------------------------------------------------

# HELM : PREMIER CHART


<br>

* namespace :

```
kubectl create ns wp
kubectl apply -f pv.yml
kubectl apply -f pvc.yml
helm install -n wp mywp bitnami/wordpress --values values.yaml
```

---------------------------------------------------------------------------------------------------

# HELM : PREMIER CHART

<br>

* liste des versions d'une chart

```
helm uninstall -n wp mywp
helm search repo bitnami/wordpress --versions
```

---------------------------------------------------------------------------------------------------

# HELM : PREMIER CHART

<br>

* installation d'une version spécifique

```
helm show values  bitnami/wordpress --version 10.4.6
helm install -n wp mywp bitnami/wordpress --values values.yaml --version 10.4.6
helm history -n wp mywp
```

---------------------------------------------------------------------------------------------------

# HELM : PREMIER CHART

<br>

* upgrade de version

```
helm upgrade -n wp mywp bitnami/wordpress --values values.yaml --version 10.10.2
```

Rq menton aura une erreur d'authentification pour mariaDB il faut lancer les commandes suggerées par helm qui definit les variables d'environne: --set variable d'env

---------------------------------------------------------------------------------------------------

# HELM : PREMIER CHART

<br>

* comparer des révisions

```
helm history -n wp mywp
helm get values -n wp mywp --revision 1
helm get values -n wp mywp --revision 2

```
# NB une release est une chart installée (instance d'une Chart), la chart est un packahe qui comprend un ensemble applicatif

