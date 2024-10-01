---
# NOTICE: Copyright 2024 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "API Contacts"
    version: "4.1.0"
    description: "API permettant de garder une trace de vos contacts et de l'entreprise pour laquelle ils travaillent."
    license: {}
    contact: {}
    termsOfService: ""
  contract:
    mediaTypes:
    - "application/json"
    sections:
    - name: "Informations générales"
      elementOrder:
      - "#/contract/texts/a7a61dca-767d-4faf-9009-6e92c85b5722"
      - "#/contract/texts/17b8246d-4fbc-4fc1-956e-3900c22b077a"
      - "#/contract/types/07f64a92-438f-4912-b459-6b4bd7c8f0cb"
    - name: "Contacts"
      description: ""
      elementOrder:
      - "#/contract/resources/1f5a9af9-cf79-4de4-8f0d-6101aa2b74ca"
      - "#/contract/resources/fd72eca2-d0be-49bb-9d91-067fa583aac5"
      - "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
    - name: "Entreprises"
      elementOrder:
      - "#/contract/resources/05aa5ca2-74ed-43b1-8742-61f987cdb645"
      - "#/contract/resources/00760e73-6bdd-4e83-880e-99b1b8709b56"
      - "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
    securitySchemes:
      "402fd110-8469-41f1-973c-60e993543efa":
        name: "HTTP_BASIC"
        type: "basic"
        description: "Toutes les méthodes GET sont publiques, ce qui signifie que *vous pouvez lire toutes les données*. Les opérations d'écriture nécessitent une authentification et sont donc interdites d'accès au public."
        describedBy: {}
    resources:
      "05aa5ca2-74ed-43b1-8742-61f987cdb645":
        path: "/companies/"
        section: "#/contract/sections/93fb48a6-7661-41b2-a9db-765478ea83a8"
        operations:
          "14d96d6a-0fb6-44f7-850c-c57f6fe44634":
            name: "Charger la liste des entreprises"
            method: "GET"
            description: "Charge une liste d'entreprises"
            tags:
            - "Entreprises"
            queryParameters:
            - type: "#/components/queryParameters/c88afd83-89dc-4700-822f-efc960d085ac"
            - type: "#/components/queryParameters/cb637446-7d85-49f6-af5a-af720dcc8836"
            - type: "#/components/queryParameters/6d008cdd-2736-473a-9c3b-23bd04eee3a8"
            - name: "name"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `name`"
              examples:
              - value: "George Street Brewery"
            responses:
              a03a6acc-5c55-4551-b67f-a88f83d0f1f4:
                status: "200"
                description: "Statut 200"
                headers:
                - type: "#/components/headers/f5b76f6a-ab0d-42e2-a5b8-8392c747e854"
                - type: "#/components/headers/07be732e-a17a-44e3-89f0-c94b5b1f1a9a"
                - type: "#/components/headers/49d5bf3e-5ef2-4b31-9e1f-4b2fea5337c9"
                - type: "#/components/headers/a1da668e-f917-495f-944c-8010fc0dee9d"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
                  examples:
                  - value: |-
                      [{
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "Brasserie",
                          "Bière",
                          "Bière anglaise"
                        ]
                      }]
              "76548ddf-7296-48b8-b079-4fe1f6f25a36":
                status: "400"
                componentName: "Statut 400"
                reference: "#/components/responses/2cfde228-ef66-4543-8d5b-72e66f1f2edc"
          "863ed14f-a684-4cc0-9f58-4159e453503b":
            name: "Créer une nouvelle entreprise"
            method: "POST"
            description: "Ajoute une entreprise"
            tags:
            - "Entreprises"
            securedBy:
            - scheme: "#/contract/securitySchemes/402fd110-8469-41f1-973c-60e993543efa"
              scopes: []
            bodies:
            - type: "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
              examples:
              - value: |-
                  {
                    "name": "George Street Brewery",
                    "address":{
                      "street": "2 place de la Defense",
                      "zipcode": "92053",
                      "city": "Paris"
                    },
                    "tags":[
                      "Brasserie",
                      "Bière",
                      "Bière anglaise"
                    ]
                  }
            responses:
              aaf9ca83-92c0-4fd1-92fb-97fa5d451219:
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
                  examples:
                  - value: |-
                      {
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "Brasserie",
                          "Bière",
                          "Bière anglaise"
                        ]
                      }
      "00760e73-6bdd-4e83-880e-99b1b8709b56":
        path: "/companies/{companyid}"
        section: "#/contract/sections/93fb48a6-7661-41b2-a9db-765478ea83a8"
        pathVariables:
        - type: "#/components/pathVariables/0e4836c6-0687-4bb3-969c-a2eec4b97519"
        operations:
          "3a4d6d24-68ba-4554-a625-5f5a0dd014e7":
            name: "Charger une entreprise"
            method: "GET"
            description: "Charge une entreprise"
            tags:
            - "Entreprises"
            responses:
              c9262051-50dd-48c7-ba0d-b8480f5ecb0c:
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
                  examples:
                  - value: |-
                      {
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "Brasserie",
                          "Bière",
                          "Bière anglaise"
                        ]
                      }
              "8ef775e8-860b-4e5e-9a4f-d011e4dfb3c6":
                status: "400"
                componentName: "Statut 400"
                reference: "#/components/responses/2cfde228-ef66-4543-8d5b-72e66f1f2edc"
          c769a0b5-058e-44ef-9de5-811f91622173:
            name: "Mettre à jour une entreprise"
            method: "PUT"
            description: "Met à jour une entreprise"
            tags:
            - "Entreprises"
            securedBy:
            - scheme: "#/contract/securitySchemes/402fd110-8469-41f1-973c-60e993543efa"
              scopes: []
            bodies:
            - type: "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
              examples:
              - value: |-
                  {
                    "name": "George Street Brewery",
                    "address":{
                      "street": "2 place de la Defense",
                      "zipcode": "92053",
                      "city": "Paris"
                    },
                    "tags":[
                      "Brasserie",
                      "Bière",
                      "Bière anglaise"
                    ]
                  }
            responses:
              "82e06491-008e-4675-b3cf-086a9bad4301":
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5"
                  examples:
                  - value: |-
                      {
                        "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
                        "name": "George Street Brewery",
                        "address":{
                          "street": "2 place de la Defense",
                          "zipcode": "92053",
                          "city": "Paris"
                        },
                        "tags":[
                          "Brasserie",
                          "Bière",
                          "Bière anglaise"
                        ]
                      }
          d00f3621-03f8-44aa-a61f-42cf26400e67:
            name: "Supprimer une entreprise"
            method: "DELETE"
            description: "Supprime une entreprise"
            tags:
            - "Entreprises"
            securedBy:
            - scheme: "#/contract/securitySchemes/402fd110-8469-41f1-973c-60e993543efa"
              scopes: []
            responses:
              "87ed6f57-3e35-4632-b354-de83907b7525":
                status: "200"
                description: "Statut 200"
      "1f5a9af9-cf79-4de4-8f0d-6101aa2b74ca":
        path: "/contacts/"
        section: "#/contract/sections/f09ba524-1802-40f4-b2a9-97c3e09fcfe7"
        operations:
          "57acb0a4-fe70-48cd-b937-1d9795f5e830":
            name: "Obtenir la liste des contacts"
            method: "GET"
            description: "Charge une liste de contacts"
            tags:
            - "Contacts"
            queryParameters:
            - type: "#/components/queryParameters/c88afd83-89dc-4700-822f-efc960d085ac"
            - type: "#/components/queryParameters/cb637446-7d85-49f6-af5a-af720dcc8836"
            - type: "#/components/queryParameters/6d008cdd-2736-473a-9c3b-23bd04eee3a8"
            - name: "firstName"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `firstName`"
              examples:
              - value: "John"
            - name: "lastName"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `lastName`"
              examples:
              - value: "Doe"
            - name: "active"
              type: "BOOLEAN"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `active`"
              examples:
              - value: true
              - value: false
            - name: "company"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `company`"
              examples:
              - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
            responses:
              "4e6be2be-f86c-46db-bd06-3c7e6c812261":
                status: "200"
                description: "Statut 200"
                headers:
                - type: "#/components/headers/f5b76f6a-ab0d-42e2-a5b8-8392c747e854"
                - type: "#/components/headers/07be732e-a17a-44e3-89f0-c94b5b1f1a9a"
                - type: "#/components/headers/49d5bf3e-5ef2-4b31-9e1f-4b2fea5337c9"
                - type: "#/components/headers/a1da668e-f917-495f-944c-8010fc0dee9d"
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
                  examples:
                  - value: |-
                      [{
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }]
              d941d168-a078-40ff-9574-bfabda00a7a3:
                status: "400"
                componentName: "Statut 400"
                reference: "#/components/responses/2cfde228-ef66-4543-8d5b-72e66f1f2edc"
          "2fb24894-6392-4844-b0f5-b9cfa69838ed":
            name: "Créer un contact"
            method: "POST"
            description: "Ajoute un contact"
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/402fd110-8469-41f1-973c-60e993543efa"
              scopes: []
            bodies:
            - type: "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
              examples:
              - value: |-
                  {
                    "firstName": "John",
                    "lastName": "Smith",
                    "birthday": 152755200000,
                    "active": true,
                    "rank": 1,
                    "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                  }
            responses:
              d6e653bb-4927-4536-ae04-091b1023080e:
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
                  examples:
                  - value: |-
                      {
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }
      fd72eca2-d0be-49bb-9d91-067fa583aac5:
        path: "/contacts/{contactid}"
        section: "#/contract/sections/f09ba524-1802-40f4-b2a9-97c3e09fcfe7"
        pathVariables:
        - type: "#/components/pathVariables/a1f0b934-1b49-4f69-9b3c-9f6b746a5669"
        operations:
          "5a9f0c0e-44ee-4803-baa3-c97df9bcc911":
            name: "Charger un contact"
            method: "GET"
            description: "Charge un contact"
            tags:
            - "Contacts"
            responses:
              b6202c4c-c4b3-4f87-9037-e2e288d4ad46:
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
                  examples:
                  - value: |-
                      {
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }
              "1b00bb9d-79a7-40e7-8d98-228ab104fecb":
                status: "400"
                componentName: "Statut 400"
                reference: "#/components/responses/2cfde228-ef66-4543-8d5b-72e66f1f2edc"
          "300b1548-2f39-4616-9559-b681b31b96ef":
            name: "Mettre à jour un contact"
            method: "PUT"
            description: "Met à jour un contact"
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/402fd110-8469-41f1-973c-60e993543efa"
              scopes: []
            bodies:
            - type: "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
              examples:
              - value: |-
                  {
                    "firstName": "John",
                    "lastName": "Smith",
                    "birthday": 152755200000,
                    "active": true,
                    "rank": 1,
                    "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                  }
            responses:
              c8f22d6b-99d8-4892-8af9-07ac6d40d64f:
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/e393291c-744a-4daf-b9bf-b0811142aef5"
                  examples:
                  - value: |-
                      {
                        "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
                        "firstName": "John",
                        "lastName": "Smith",
                        "birthday": 152755200000,
                        "active": true,
                        "rank": 1,
                        "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
                      }
          e94ecaf7-9291-4907-85e4-2c6081b7cead:
            name: "Supprimer un contact"
            method: "DELETE"
            description: "Supprime un contact"
            tags:
            - "Contacts"
            securedBy:
            - scheme: "#/contract/securitySchemes/402fd110-8469-41f1-973c-60e993543efa"
              scopes: []
            responses:
              e948237b-ef01-4f18-8558-7abb39213877:
                status: "200"
                description: "Statut 200"
    types:
      "5bfe6d0e-811e-4b4f-a448-a3aca1eb00b5":
        name: "Entreprise"
        type: "OBJECT"
        description: "Type de données d'une entreprise"
        section: "#/contract/sections/93fb48a6-7661-41b2-a9db-765478ea83a8"
        properties:
        - name: "id"
          type: "STRING"
          description: "Champ de clé primaire auto-généré"
          required: true
        - name: "name"
          type: "STRING"
          required: true
        - name: "tags"
          type: "ARRAY"
          items:
            type: "STRING"
            pattern: "[a-zA-Z]+"
          examples:
          - value: "[\"Brasserie\", \"Bière\", \"Bière anglaise\"]"
        - name: "address"
          type: "OBJECT"
          required: true
          properties:
          - name: "street"
            type: "STRING"
            required: true
          - name: "city"
            type: "STRING"
            required: true
          - name: "zipcode"
            type: "STRING"
            required: true
            pattern: "[0-9]*"
        examples:
        - value: |-
            {
              "id": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f",
              "name": "George Street Brewery",
              "address":{
                "street": "2 place de la Defense",
                "zipcode": "92053",
                "city": "Paris"
              },
              "tags":[
                "Brasserie",
                "Bière",
                "Bière anglaise"
              ]
            }
      e393291c-744a-4daf-b9bf-b0811142aef5:
        name: "Contact"
        type: "OBJECT"
        description: "Type de données d'un contact"
        section: "#/contract/sections/f09ba524-1802-40f4-b2a9-97c3e09fcfe7"
        properties:
        - name: "id"
          type: "STRING"
          description: "Champ de clé primaire auto-généré"
          required: true
          examples:
          - value: "0e8ffb10-ad98-11e6-bf2e-47644ada7c0f"
        - name: "firstName"
          type: "STRING"
          required: true
          examples:
          - value: "Kurt"
        - name: "lastName"
          type: "STRING"
          required: true
          examples:
          - value: "Williams"
        - name: "birthday"
          type: "INTEGER"
          format: "INT64"
          description: "Date de naissance en horodatage Unix (en ms)"
          examples:
          - value: 173664000000
          - value: 383270400000
        - name: "active"
          type: "BOOLEAN"
          default: true
        - name: "rank"
          type: "INTEGER"
          format: "INT32"
          minimum: 1
          examples:
          - value: 1
          - value: 2
          - value: 3
        - name: "company"
          type: "STRING"
          description: "Cette propriété fait référence à Company."
          examples:
          - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
        examples:
        - value: |-
            {
              "id": "0e8dd830-ad98-11e6-bf2e-47644ada7c0f",
              "firstName": "John",
              "lastName": "Smith",
              "birthday": 152755200000,
              "active": true,
              "rank": 1,
              "company": "0e8cedd0-ad98-11e6-bf2e-47644ada7c0f"
            }
      "07f64a92-438f-4912-b459-6b4bd7c8f0cb":
        name: "Erreur"
        type: "OBJECT"
        description: "Cette structure générale d'erreur est utilisée à travers toute l'API."
        section: "#/contract/sections/8b0af576-7b8f-4297-abc4-cb97bf2aaeee"
        properties:
        - name: "code"
          type: "INTEGER"
          required: true
          minimum: 400
          maximum: 599
        - name: "description"
          type: "STRING"
          examples:
          - value: "Paramètre de requête invalide [$size]\_: valeur entière invalide [abc]"
          - value: "Le serveur a compris la requête mais refuse de l'exécuter."
        - name: "reasonPhrase"
          type: "STRING"
          examples:
          - value: "Bad Request"
          - value: "Forbidden"
        examples:
        - value: |-
            {
              "code": 400,
              "description": "Paramètre de requête invalide [$size] : valeur entière invalide [abc]",
              "reasonPhrase": "Bad Request"
            }
    texts:
      a7a61dca-767d-4faf-9009-6e92c85b5722:
        title: "Authentification"
        content: |-
          Cette API est sécurisée par authentification Basic.

          Toutes **les opérations de lecture sont ouvertes** et ne nécessitent pas d'authentification. Cependant, toutes **les opérations d'écriture nécessitent une authentification**.
        section: "#/contract/sections/8b0af576-7b8f-4297-abc4-cb97bf2aaeee"
      "17b8246d-4fbc-4fc1-956e-3900c22b077a":
        title: "Gestion des erreurs"
        content: |+
          Cette API utilise des codes de statut HTTP standards pour indiquer le statut d'une réponse.

          Il y a deux catégories principales de réponses d'erreur. La structure du payload de réponse de chacune est différente.

          * Erreurs simples
          * Erreurs détaillées


          # Erreurs simples

          | Nom | Code | Description |
          | -------- | -------- | -------- |
          | Bad request     | 400     | Requête incorrecte.     |
          | Unauthorized     | 401     | Une authentification est nécessaire pour accéder à la ressource.     |
          | Forbidden     | 403     | Le serveur a compris la requête mais refuse de l'exécuter.     |
          | Not Found     | 404     | Le serveur n'a trouvé aucune ressource correspondant à l'URI de la requête.     |
          | Not acceptable     | 406     | Le serveur ne peut retourner de réponse au format demandé par le client.     |
          | Unsupported Media Type     | 415     | Le serveur refuse de traiter la requête car l'entité de la requête est dans un format non supporté par la ressource interrogée pour la méthode interrogée.     |
          Maximum de requêtes dépassé     | 429     | Le client a émis trop de requêtes dans un délai donné.     |
          | Server error     | 500     | Une erreur technique est survenue.  |






          # Erreurs détaillées
          | Nom | Code | Description |
          | -------- | -------- | -------- |
          | Unprocessable entity     | 422     | Le serveur comprend le type de contenu de l'entité de la requête et sa syntaxe est correcte, mais le traitement des instructions contenues a échoué.     |




        section: "#/contract/sections/8b0af576-7b8f-4297-abc4-cb97bf2aaeee"
  components:
    pathVariables:
      a1f0b934-1b49-4f69-9b3c-9f6b746a5669:
        name: "contactid"
        componentName: "contactid"
        type: "STRING"
        description: "Identifiant du contact"
        required: true
        examples:
        - value: "0e8dd830-ad98-11e6-bf2e-47644ada7c0f"
      "0e4836c6-0687-4bb3-969c-a2eec4b97519":
        name: "companyid"
        componentName: "companyid"
        type: "STRING"
        description: "Identifiant de l'entreprise"
        required: true
        examples:
        - value: "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f"
    queryParameters:
      c88afd83-89dc-4700-822f-efc960d085ac:
        name: "$size"
        componentName: "$size"
        type: "INTEGER"
        description: "Taille de la page à récupérer."
        examples:
        - value: 10
      cb637446-7d85-49f6-af5a-af720dcc8836:
        name: "$page"
        componentName: "$page"
        type: "INTEGER"
        description: "Numéro de la page à récupérer."
        examples:
        - value: 1
        - value: 42
      "6d008cdd-2736-473a-9c3b-23bd04eee3a8":
        name: "$sort"
        componentName: "$sort"
        type: "STRING"
        description: "Ordre dans lequel récupérer les résultats. Plusieurs critères de tri peuvent être passés."
        examples:
        - value: "birthday DESC"
        - value: "birthday ASC,rank DESC"
    headers:
      f5b76f6a-ab0d-42e2-a5b8-8392c747e854:
        name: "X-Page-Count"
        componentName: "X-Page-Count"
        type: "INTEGER"
        examples:
        - value: 1
      "07be732e-a17a-44e3-89f0-c94b5b1f1a9a":
        name: "X-Page-Number"
        componentName: "X-Page-Number"
        type: "INTEGER"
        examples:
        - value: 1
      "49d5bf3e-5ef2-4b31-9e1f-4b2fea5337c9":
        name: "X-Page-Size"
        componentName: "X-Page-Size"
        type: "INTEGER"
        examples:
        - value: 25
      a1da668e-f917-495f-944c-8010fc0dee9d:
        name: "X-Total-Count"
        componentName: "X-Total-Count"
        type: "INTEGER"
        examples:
        - value: 2
    responses:
      "2cfde228-ef66-4543-8d5b-72e66f1f2edc":
        status: "400"
        componentName: "Statut 400"
        bodies:
        - type: "#/contract/types/07f64a92-438f-4912-b459-6b4bd7c8f0cb"
          mediaTypes:
          - "application/json"
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "API Contacts 4.1.0",
        "description" : "API permettant de garder une trace de vos contacts et de l'entreprise pour laquelle ils travaillent.",
        "importedFrom" : "1a22c7a2-d831-4eb2-b7ad-5b15520bd9ad"
      },
      "children" : [ {
        "entity" : {
          "type" : "Service",
          "name" : "Informations générales"
        }
      }, {
        "entity" : {
          "type" : "Service",
          "name" : "Contacts",
          "description" : ""
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "57acb0a4-fe70-48cd-b937-1d9795f5e830",
            "name" : "Obtenir la liste des contacts",
            "description" : "Charge une liste de contacts",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "$size",
                  "value" : "10",
                  "enabled" : false
                }, {
                  "name" : "$page",
                  "value" : "1",
                  "enabled" : false
                }, {
                  "name" : "$sort",
                  "value" : "birthday DESC",
                  "enabled" : false
                }, {
                  "name" : "firstName",
                  "value" : "John",
                  "enabled" : false
                }, {
                  "name" : "lastName",
                  "value" : "Doe",
                  "enabled" : false
                }, {
                  "name" : "active",
                  "value" : "true",
                  "enabled" : false
                }, {
                  "name" : "company",
                  "value" : "0e8c9fb0-ad98-11e6-bf2e-47644ada7c0f",
                  "enabled" : false
                } ]
              }
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "uriEditor" : true
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "2fb24894-6392-4844-b0f5-b9cfa69838ed",
            "name" : "Créer un contact",
            "description" : "Ajoute un contact",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/"
            },
            "method" : {
              "link" : "",
              "name" : "POST",
              "requestBody" : true
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Content-Type",
              "value" : "application/json"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : "{\n  \"firstName\": \"John\",\n  \"lastName\": \"Smith\",\n  \"birthday\": 152755200000,\n  \"active\": true,\n  \"rank\": 1,\n  \"company\": \"0e8cedd0-ad98-11e6-bf2e-47644ada7c0f\"\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "5a9f0c0e-44ee-4803-baa3-c97df9bcc911",
            "name" : "Charger un contact",
            "description" : "Charge un contact",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/{contactid}"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form"
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "300b1548-2f39-4616-9559-b681b31b96ef",
            "name" : "Mettre à jour un contact",
            "description" : "Met à jour un contact",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/{contactid}"
            },
            "method" : {
              "link" : "",
              "name" : "PUT",
              "requestBody" : true
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Content-Type",
              "value" : "application/json"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : "{\n  \"firstName\": \"John\",\n  \"lastName\": \"Smith\",\n  \"birthday\": 152755200000,\n  \"active\": true,\n  \"rank\": 1,\n  \"company\": \"0e8cedd0-ad98-11e6-bf2e-47644ada7c0f\"\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "e94ecaf7-9291-4907-85e4-2c6081b7cead",
            "name" : "Supprimer un contact",
            "description" : "Supprime un contact",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/contacts/{contactid}"
            },
            "method" : {
              "link" : "",
              "name" : "DELETE"
            },
            "headers" : [ ],
            "headersType" : "Form"
          }
        } ]
      }, {
        "entity" : {
          "type" : "Service",
          "name" : "Entreprises"
        },
        "children" : [ {
          "entity" : {
            "type" : "Request",
            "id" : "14d96d6a-0fb6-44f7-850c-c57f6fe44634",
            "name" : "Charger la liste des entreprises",
            "description" : "Charge une liste d'entreprises",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/",
              "query" : {
                "delimiter" : "&",
                "items" : [ {
                  "name" : "$size",
                  "value" : "10",
                  "enabled" : false
                }, {
                  "name" : "$page",
                  "value" : "1",
                  "enabled" : false
                }, {
                  "name" : "$sort",
                  "value" : "birthday DESC",
                  "enabled" : false
                }, {
                  "name" : "name",
                  "value" : "George Street Brewery",
                  "enabled" : false
                } ]
              }
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "uriEditor" : true
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "863ed14f-a684-4cc0-9f58-4159e453503b",
            "name" : "Créer une nouvelle entreprise",
            "description" : "Ajoute une entreprise",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/"
            },
            "method" : {
              "link" : "",
              "name" : "POST",
              "requestBody" : true
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Content-Type",
              "value" : "application/json"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : "{\n  \"name\": \"George Street Brewery\",\n  \"address\":{\n    \"street\": \"2 place de la Defense\",\n    \"zipcode\": \"92053\",\n    \"city\": \"Paris\"\n  },\n  \"tags\":[\n    \"Brasserie\",\n    \"Bière\",\n    \"Bière anglaise\"\n  ]\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "3a4d6d24-68ba-4554-a625-5f5a0dd014e7",
            "name" : "Charger une entreprise",
            "description" : "Charge une entreprise",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/{companyid}"
            },
            "method" : {
              "link" : "",
              "name" : "GET"
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form"
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "c769a0b5-058e-44ef-9de5-811f91622173",
            "name" : "Mettre à jour une entreprise",
            "description" : "Met à jour une entreprise",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/{companyid}"
            },
            "method" : {
              "link" : "",
              "name" : "PUT",
              "requestBody" : true
            },
            "headers" : [ {
              "enabled" : true,
              "name" : "Content-Type",
              "value" : "application/json"
            }, {
              "enabled" : true,
              "name" : "Accept",
              "value" : "application/json"
            } ],
            "headersType" : "Form",
            "body" : {
              "bodyType" : "Text",
              "textBody" : "{\n  \"name\": \"George Street Brewery\",\n  \"address\":{\n    \"street\": \"2 place de la Defense\",\n    \"zipcode\": \"92053\",\n    \"city\": \"Paris\"\n  },\n  \"tags\":[\n    \"Brasserie\",\n    \"Bière\",\n    \"Bière anglaise\"\n  ]\n}"
            }
          }
        }, {
          "entity" : {
            "type" : "Request",
            "id" : "d00f3621-03f8-44aa-a61f-42cf26400e67",
            "name" : "Supprimer une entreprise",
            "description" : "Supprime une entreprise",
            "uri" : {
              "host" : "${\"BaseUrl\"}",
              "path" : "/companies/{companyid}"
            },
            "method" : {
              "link" : "",
              "name" : "DELETE"
            },
            "headers" : [ ],
            "headersType" : "Form"
          }
        } ]
      } ]
    } ],
    "environments" : [ {
      "name" : "API Contacts 4.1.0",
      "importedFrom" : {
        "projectId" : "1a22c7a2-d831-4eb2-b7ad-5b15520bd9ad"
      },
      "variables" : {
        "7d77dbc8-a635-452c-845e-9475403c2088" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
