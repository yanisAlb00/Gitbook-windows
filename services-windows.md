# Services Windows

{% embed url="https://www.malekal.com/processus-service-windows/" %}

## Définition d'un service

Un service Windows est donc un programme qui peut démarrer automatiquement lors du lancement du système d’exploitation, sans nécessiter l’intervention d’un utilisateur ou la connexion à un compte du serveur.

## Gestion des services

* Sur votre clavier, appuyez sur la touche Windows + R
* dans la fenêtre exécutez, saisissez **services.msc**
* Enfin cliquez sur OK.

L'utilitaire msconfig permet également de désactiver les services Microsoft.

&#x20;Les services Windows utilisateurs démarrent avec le compte local. Mais certains services peuvent démarrer avec un compte plus élevés du type AUTORITE/NT. Il s’agit d’un utilisateur système avec les permissions les plus importantes.\
\
La commande sc permet de gérer les services en ligne de commande.

## Dépendances

Dans l'utilitaire services.msc , on peut lister les services qui dépendent d'un certain service et également les services auxquels il dépend (clique-droit / Propriétés) :\
\
![](<.gitbook/assets/image (1).png>)\


## Les services dans la base de registre

Un service est chargé au démarrage de Windows par le processus svchost.exe. Si un service est démarré directement par Windows, il se trouve dans la clef suivante de la base de registre :

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\servicename
```

La base de registre est accessible via :

* Sur votre clavier, appuyez sur la touche Windows  + R
* Dans la fenêtre exécutez, saisissez **regedit** puis **OK**.

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

![](<.gitbook/assets/image (2).png>)\


La clef _Start_ qui permet de définir le type de démarrage, ainsi la valeur :

* 2 permet un démarrage de type automatique
* 3 permet un démarrage de type manuel
* 4 permet de rendre le service désactivé

## Svchost.exe

svchost.exe est le processus système de Windows qui gère les groupes de services.

Sur un Windows il existe beaucoup de groupes de services et donc on peut avoir des dizaines de processus svchost.exe Cela est tout à fait normal.

Une liste de ces groupes et services peut être trouvé dans la base de registre à la clef suivante :\


```
HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion\Svchost
```

![](<.gitbook/assets/image (4).png>)

Exemple de commande qui permet de lancer tous les services dans le groupe netsvcs :

```
svchost.exe -k groupe - ex svchost.exe -k netsvcs
```

A chaque fois qu'un nouveau groupe est chargé par svchost.exe , alors un nouveau processus svchost.exe s'affiche dans le gestionnaire de tâches.

