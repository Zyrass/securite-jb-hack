# Cas n° 4

## Q1 RECON_00 - Retrouve le contenu du fichier robots.txt du site principal de Hackycorp.

```md
## Réponse

- [X] - URL :  https://hackycorp.com/robots.txt
```
Le code retourner

```txt
User-agent: *
Disallow: /

# You solved recon_00
# The key for this challenge is
# af9c328a-02b4-439d-91c6-f46ab4a0835b
```

## Q2 RECON_01 - Souvent, les pages d’erreur mal configurées révèlent de précieuses information. Que remarques-tu sur le site principal ?

```md
## Réponse

- [X] - URL :  https://hackycorp.com/dfsdfsdf
```
Page web retourner
```html
<html>
    <head></head>
    <body>
        <h1>404 page! You solved recon_01</h1>
        The key for this challenge is: aeaee57f-2a82-41da-bc4c-d081c8cddfc8
    </body>
</html>
```

## Q3 RECON_02 - De nombreux sites web contiennent, à la racine, un fichier security.txt permettant de dire aux chercheurs en sécurité comment faire remonter une information sur une faille ou une vulnérabilité. Mais est-ce vraiment une bonne idée ?

```md
## Réponse

- [X] - URL :  http://0x00.a.hackycorp.com/
- [x] - Bonne pratique : 
            OUI, malgré tout, il s'agit d'une aide à la résolution des failles critiques.
```
le code est une image récupérable à cette adresse : http://0x00.a.hackycorp.com/logo.png

## Q4 RECON_03 - Tu vas maintenant profiter d’une mauvaise configuration des serveurs web encore très courante : le directory listing. Elle te permettra de trouver, sur le site principal, un répertoire dont tu peux découvrir le contenu.

> https://hackycorp.com/images/key.txt

```txt
Nice find! You solved recon_03

The key for this challenge is 93790afa-6985-47fd-b564-aa7ba59ed6a9
```

## Q5 RECON_04 - Tu vas pouvoir tenter de deviner le nom d’un répertoire couramment utilisé pour les pages d’administration. En effet, avant de lancer un brute-force sur l’arborescence d’un D34 : Sécurité web opérationnelle et investigation numérique Critère de diffusion : RESTREINT - Page 7 / 10 site web, il est souvent payant de tester les noms de répertoires les plus communément répandus (applications connues, outils du marché).

> https://hackycorp.com/admin/

```html
<html>
    <head></head>
    <body>
        <h1>Well done! You solved recon_04</h1>

        The key for this exercise is: ad1d44d6-ab73-4640-8291-c5bf2343e2a5
    </body>
</html>
```

## Q6 RECON_05 - Dans cet exercice, tu vas tenter de trouver un répertoire qui n’est pas directement accessible. Dans ce cas, des outils comme **patator**, **FFUF** ou **WFuzz** vous seront utiles.

## Q7 RECON_06 - Sauras-tu trouver le virtualhost par défaut du serveur principal ?

## Q8 RECON_07 - Même chose que précédemment, mais avec le virtualhost par défaut du serveur principal sur transport TLS

> https://balancer.hackycorp.com/

```html
<html>
    <head></head>
    <body>
        <h1>Well done! You solved recon_07</h1>

        The key for this exercise is 23eafa56-6d55-4b78-8307-24e7dc2ce5e6
    </body>
</html>
```

## 9 - Dans cet exercice, nous allons nous intéresser aux entêtes de la réponse HTTP.

```md
## Réponse:
> Lorsqu'on inspect le code, dans la partie réseau une fois rafraichi, je me déplace dans la partie "en-têtes de réponse" et je peux y trouver :

Pentesterlab_recon_09: 99d0738b-1e52-4a00-8885-b15894b2c79e
```

## 10 - Dans cet exercice, nous nous intéressons aux noms alternatifs présents dans le certificat du site. Utilise ton navigateur ou encore openssl…

## 11 - Dans cet exercice, tu vas effectuer une reconnaissance visuelle pour retrouver l’application avec la clé en rouge.

```md
    Les applications sont hébergées selon le schéma suivant :
```

```diff
- 0x["%02x"].a.hackycorp.com comme par exemple :
- . 0x00.a.hackycorp.com
- . 0x01.a.hackycorp.com
- . ...
- . 0x0a.a.hackycorp.com
- . 0x0b.a.hackycorp.com
- . …

Il sera bien sûr nécessaire d’automatiser ta recherche…
```

## 12 - Il s’agit maintenant de brute forcer un virtualhost en manipulant l’entête Host. Il n’y a pas de résolution DNS sur cet hôte. Tu dois donc ciblé hackycorp.com et bruteforcer le virtualhost qui termine par .hackycorp.com.

## 13 - Accède maintenant au load balancer sur balancer.hackycorp.com.

> Il est souvent interessant pour un assaillant d’émettre de multiples fois une même requête
> afin de découvrir si plusieurs back sont impliqués dans son traitement.

## 14 - Intéresse-toi aux enregistrements DNS TXT de key.z.hackycorp.com.

> Les enregistrements TXT contiennent régulièrement des informations précieuses…

## 15 - Dans cet exercice, tu vas étudier les transferts de zone

> Ils sont souvent utilisés pour synchroniser de multiples serveurs DNS. Une liste prédéfinie
> des hôtes autorisés à effectuer cette opération devrait être définie, mais ce n’est pas
> toujours le cas, et il est possible d’avoir accès à de nouveaux hôtes.

Tu effectueras un transfert de zone pour z.hackycorp.com

## 16 - Est-il possible d’effectuer un transfert de la zone interne nommée « int » en utilisant le serveur de noms de z.hackycorp.com ?

> Tu verras qu’il est parfois possible d’accéder aux informations d’une zone interne en
> passant par des serveurs publics.

## 17 - Est-il possible de connaître la version de Bind exécutée sur le serveur z.hackycorp.com.

> Imaginons maintenant qu’un assaillant prépare une campagne de phishing contre les
> développeurs de ton équipe (https://github.com/hackycorp) :

## 18 - Est-il possible de trouver le nom du développeur qui a « commit » le code du dépôt « test1 » sur GitHub ? Quel est-il ?

**Hacky Dev**

## 19 - Ce développeur possède-t-il des dépôts publics ? Si oui, laisse-t-il trainer des informations sensibles ?






## 20 - Trop souvent encore, les développeurs fonts des commits avec une mauvaise adresse e-mail, ce qui peut conduire à faire fuite des adresses personnelles ou encore des comptes systèmes. Trouveras-vous une adresse différente des autres dans le dépôt « repo7 » ?

> Astuce : la commande « git log » en local est ton amie.

commit 98b4472d5e46af145968345b262bc930c4b8c6e3
Author: Hacky Dev <9590c69b-f9d0-469d-9475-827bf0e1126e@hackycorp.com>
Date: Wed Nov 18 10:49:08 2020 +1100

## 21 - Cette fois-ci, rien de sensible n’a été laissé par les développeurs dans le code source de la branche « master » du dépôt « repo4 ». Mais il y a souvent d’autres branches …

> https://github.com/hackycorp/repo4/blob/test/KEY

This is the key for recon 21: a60b4aee-642a-483b-9262-ccfc2ed46f0d

## 22 - Souvent, lorsqu’on publie accidentellement une information sensible sur Github, on supprime cette information du code local puis on effectue un nouveau commit. Est-ce une bonne idée ? NON. Sauras-tu trouver les informations qui ont été supprimées dans le dépôt « repo9 » ?

> Astuce : l’outil en ligne de commande « tic » en local est ton ami

https://github.com/hackycorp/repo9/commit/e8fec2d079cf9bfdf782a9ce4aab8ae8ce947548#diff-41a373ea209131c2ac8f7ae4305bc1e92c108e6bcd976bd41bc9ef0d3547ca84

This is the key for RECON_22: 3ee505c2-8aa9-4d5e-810e-921778dce1e6

## 23 - De même, les messages de commits peuvent contenir de précieuses informations… Regarde du côté du dépôt « repo0a ».

https://github.com/hackycorp/repo0a/commit/a35a9174f3a6238a8ad70c549287d09e258f087b
Another test
This is the key for RECON_23: 5c75cfe9-52dd-475b-8cfa-7ffc492abeca

> Astuce : ici encore, l’outil en ligne de commande « tic » en local est ton ami.

Revenons maintenant aux pratiques de coding de ton équipe :

## 24 - Dans cette exercice, nous allons nous intéresser aux fichiers statiques disponibles publiquement sur les serveurs d’assets (Javascript, CSS,…). Il existe un fichier key.txt quelque part.




## 25 - Dans cet exercice, nous allons vérifier si les développeurs que tu encadres font parfois preuve de flemme quant à la manipulation des mots de passe et autres informations sensibles et qui « hard codent » certaines d’entre elles. Effectue une code review du Javascript.

> Astuce: tu recherches la valeur de la clé ptlab_key_recon_26.

https://assets.hackycorp.com/js/script.js
ptlab_key_recon_26: 'd6b75269-97a3-44de-be32-fff0dd55e7ef',

## 26 - BILAN - À partir de tous les cas de figure passés en revue dans l’étude de cas N°4, tu es en mesure de déduire un ensemble de points de vigilance et de bonnes pratiques à mettre en oeuvre au niveau de ton équipe pour renforcer la sécurité. Tu dresseras une liste des actions à entreprendre et tu la reporteras dans le fichier « answers.md ».



