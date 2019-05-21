# Développement de bundle OSGi


## Exercices

1. Creer un bundle 'tuto_esb_ws_portal' ayant les endpoints REST suivant (utilisant les composants tRestRequest/tRestResponse)
  a. GET '/tuto/portal/hello'
  Retourne un string 'Hello, world' avec un HTTP code 200.
  
  b. GET '/tuto/portal/hello/{user}
  Avec un parametre user = "John", retourne un string 'Hello, John.' avec un HTTP code 200 et un erreur body 'bad request' code 500 si user contient des caracters non alphabetiques.
  
  c. POST '/tuto/portal/currency' application/json
  Payload:
  {
    "from": "EUR",
    "to": "USD"
  }
  
  Appelle https://api.exchangeratesapi.io/latest puis retourne 200 application/json:
  {
   "rate": "1.1167",
   "date": "dd/mm/yyyy"
  }
  
  Cas d'erreurs:
  - bad format: 400 {"error": "bad format"}
  - internal error: 500 {"error": "Sorry, we had internal issue."}
  
2. a. Creer un bundle 'tuto_esb_ws_delegator' avec une route qui recoit en entree une requete http de type POST avec un paylod quelconque et empile le payload dans un queue 'delegator_tasks' de ActiveMQ.
   b. Creer un bundle 'tuto_esb_processor' qui depile la queue 'delegator_tasks' et append le contenu dans un fichier.
