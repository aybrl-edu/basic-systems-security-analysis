# Basic Systems Security Analysis
Basic techniques for systems security analysis

## Table of Contents
1. [Description d'analyse](#Description-d'analyse)
2. [Identification des vulnérabilités](#Identification-des-vulnérabilités)
3. [Third Example](#third-example)
4. [Références](#Références)

## Description d'analyse

On va lancer une analyse de sécurité sur l'application web sous le répertoire /vul-app. Dans le rapport suivant on détaillera l'impact de chaque vulnérabilité detecté ainsi que l'application d'un correctif qui nous permettera de se protéger de cette dernière. La nouvelle version sécurisée de l'application sera sous le répertoire /sec-app. Des tests d'efficacité des correctifs apportés seront faits sur la nouvelle version et seront détaillés également dans ce rapport.

## Identification des vulnérabilités

### Injections SQL

#### 1- Select

Entrant la chaine de caractères suivantes : 

``` 20000' # ```

On s'apperçoit qu'on peut accèder aux données de l'utilisateur ayant l'id 20000 sans devoir saisir un mot de passe. Cela prouve que notre application est vulnérable contre des injections SQL de type SELECT

![image](https://user-images.githubusercontent.com/114408910/206226217-bf16b4c3-28b4-433b-be57-656588fd91a3.png)

#### 2- Update

On va essayer de mettre à jour le salaire d'un utilisateur avec une injection SQL. Pour cela, on suppose qu'on pocéde l'id et le mot de passe de l'utilisateur. On va accèder au profil de l'utilisateur et on va se mettre sur la page de la mise à jour du profil. On va exécuter cet exemple sur Ryan ayant l'id 30000.

On récupére tout d'abord son salaire initial

![image](https://user-images.githubusercontent.com/114408910/206229400-fd7278a9-bfad-4ee6-946a-f93433343f91.png)

Puis on essyera avec une injection SQL à partir de la page de mise à jour de mettre à jour son salaire.

``` Rich_Ryan', Salary=10000000;# ```

![image](https://user-images.githubusercontent.com/114408910/206233299-a98c7465-f347-48fc-bcbb-379c7f843291.png)

=> Notre application est vulnérable aux différentes types des injections SQL

## Références
<ol>
  <li>Droits d'accès aux bases de données : https://www.ibm.com/docs/en/informix-servers/12.10?topic=statement-database-level-privileges </li>
</ol>
