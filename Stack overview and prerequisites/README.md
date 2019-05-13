# Stack overview and prerequisites

## Talend, c'est quoi au juste ?

C'est une plateforme d'*intégration de données* qui, depuis sa création en 2005, n'a cessé de s'élargir pour devenir le leader dans son domaine. L'intégration de données est un processus dans lequel des donnnées hétérogènes issues de différentes sources sont extraites, combinées, structurées et incorporées dans un seul entrepot (généralement data warehouse mais format de destination dépendant du design et du besoin). Ce processus, incluant le nettoyage de donnée  et mappage *ETL*, devient un élement stratégique pour produire des analytiques efficaces et d'intélligence d'affaire opérationnelle.

 Si au tout début, leur produit est un logiciel unique aujourd'hui connu sous le nom de "Talend Open Studio fro Data Integration", actuellement c'est une suite de solution incluant entre autres la gestion, la préparation, le stockage données, l'intégration d'application entreprise.




## Trop de *buzzwords*, présentez moi des scénarios d'utilisation ?
Chez eTech, nous utilisons Talend principalement pour deux choses: 
1. **Traitement en batch de données automatisé et planifié** (cron) sur Jenkins (Open Studio) ou TAC (Entreprise). Par exemple, un client nous a confié le developpement et la migration de son site vers une nouvelle plateforme utilisant le stack suivant pour le backend: Symfony, Neo4j, LDAP. Et naturellement, ceci inclue la migration de leurs données. Que feriez-vous si vous aurez en main quelques dumps CSV de tables relationnelles inconsistents et médiocrement structurés à importer vers cette nouvelle plateforme dans lequel un champ unique d'un table MySQL doit impérativement figurer dans LDAP et Neo4j doit avoir une vue graph? Talend était la solution.
Dans un autre exemple, on devait approvisionner quotidiennement le catalogue d'un Marketplace sous Magento. Le hic c'est que les sources, et par conséquent les formats, des données sont hétérogènes; un fournisseur utilise encore du SOAP (un tech aussi antique que Rome, mais sans la beauté époustouflante) tandis que d'autres un RESTful webservice. En amont, vous aurez donc plusieurs fichiers interdépendants, certains en XML, d'autres en JSON et vous devriez tout faire pour qu'à la sortie vous aurez un format acceptable par Magento. Cool, maintenant ils ont décidé de remplacer Magento par Odoo! Vous aurez sans doute une idée de la quantité de cheveux que vous vous arracheriez si vous devriez developper tout cela à la main.
<p align="center">
  <img width="500" height="280" src="screenshot/gummo-spaghetti.jpeg">
</p>
<p align="center">
    <em>Vous et votre code spaghetti sans Talend</em>
</p>

2. **Un portail applicatif d'échange de données entre différentes parties (ESB)** Un besoin a été satisfait en déployant quelques bundles developpés sous Talend dans Apache Karaf. Ce besoin consiste à trouver une solution permettant un système ERP de communiquer d'une manière non bloquant mais toutefois temps réel à plusieurs autres sites dont les URI et le payload des services web sont dynamique! Dans un autre projet, on utilise Talend ESB pour relier plusieurs bases de données Odoo en synchronisant, entre autres, les catégories, produits, commande, facture sans parler des modèles personnalisés. Ajoutant compléxité, un data mart doit être approvisionné et d'autre parties joignent à la danse, cette fois par échanges FTP.


Dans un future très proche, nous espérons envahir le monde du BigData auquel Talend se trouve particulièrement efficace en générant des codes prêts à tourner sous Hadoop/Spark.

A ce stade, vous devez avoir une vision un peu plus claire de ce que vous allez apprendre. 