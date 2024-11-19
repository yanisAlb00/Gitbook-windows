# ADMiner

Outil d'audit et de contrôle continu des vulnérabilités d'un environnement Active Directory.\
\
Utilisation de la représentation en graphe (comme BloodHound) pour schématiser les chemins de compromission au sein de l'AD.\
\
ADMiner s'appuie sur une collecte de données SharpHound (neo4j)

{% hint style="info" %}
Pareil pour BloodHound, il est nécessaire de collecter des données (avec SharpHound , par exemple)
{% endhint %}

Exemple de chemin de contrôle :&#x20;

* Alpha est administrateur local d'un serveur
* Sur ce même serveur, un domain admin est loggé
* Si on compromet Alpha, on peut récupérer les credentials du domain admin

Utilisation de requêtes Cipher (langage naturel proche du SQL) qui permet d'utiliser les relations associées à un objet pour trouver des chemins dans l'AD.\
\
ADMiner est développé en Python pour interagir avec la base neo4j\
\
Point non présent dans BloodHound : Historisation des objets (l'analyse stocke l'état dans un fichier JSON et l'outil est capable de comparer l'état d'un objet entre 2 collectes)\
\
