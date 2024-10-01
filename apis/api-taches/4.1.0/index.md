---
# NOTICE: Copyright 2024 Talend SA, Talend, Inc., and affiliates. All Rights Reserved. Customer’s use of the software contained herein is subject to the terms and conditions of the Agreement between Customer and Talend.
layout: "apiDefinition_1.1.0"
api-definition:
  specVersion: "4.1.0"
  info:
    name: "API Tâches"
    version: "4.1.0"
    description: "Une API pour gérer une liste de tâches à effectuer."
    license: {}
    contact: {}
    termsOfService: ""
  contract:
    mediaTypes:
    - "application/json"
    unsortedElementOrder:
    - "#/contract/resources/8f242d2e-3dd3-41d2-8b10-a413646b64f5"
    - "#/contract/resources/37bbd4ac-4055-4b68-b87e-42f4593cecaa"
    - "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
    - "#/contract/types/2d2b154f-87f1-4433-a1c6-bd883ee7d9a7"
    securitySchemes:
      e95bce1c-b92c-4c6e-90b8-63c49689a29d:
        name: "HTTP_BASIC"
        type: "basic"
        description: "Toutes les méthodes GET sont publiques, ce qui signifie que *vous pouvez lire toutes les données*. Les opérations d'écriture nécessitent une authentification et sont donc interdites d'accès au public."
    resources:
      "8f242d2e-3dd3-41d2-8b10-a413646b64f5":
        path: "/tasks/"
        operations:
          ce9e46f7-f00e-4a19-be29-6468ceff67ca:
            name: "Charger la liste des tâches"
            method: "GET"
            queryParameters:
            - name: "$size"
              type: "INTEGER"
              description: "Taille de la page à récupérer."
              examples:
              - value: 10
            - name: "$page"
              type: "INTEGER"
              description: "Numéro de la page à récupérer."
              examples:
              - value: 1
            - name: "$sort"
              type: "STRING"
              description: "Ordre dans lequel récupérer les résultats. Plusieurs critères de tri peuvent être passés."
              examples:
              - value: "createdAt DESC"
              - value: "name ASC"
            - name: "id"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `id`"
              examples:
              - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
            - name: "name"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `name`"
              examples:
              - value: "En savoir plus sur les API"
            - name: "createdAt"
              type: "STRING"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `createdAt`"
              examples:
              - value: "2016.07.03"
            - name: "completed"
              type: "BOOLEAN"
              description: "Permet de filtrer la collection de résultats sur la valeur du champ `completed`"
              examples:
              - value: true
              - value: false
            responses:
              "6650c6a3-747e-4506-ad5f-cb0b6bf46359":
                status: "200"
                description: "Statut 200"
                headers:
                - name: "X-Page-Count"
                  type: "INTEGER"
                  examples:
                  - value: 1
                - name: "X-Page-Number"
                  type: "INTEGER"
                  examples:
                  - value: 1
                - name: "X-Page-Size"
                  type: "INTEGER"
                  examples:
                  - value: 25
                - name: "X-Total-Count"
                  type: "INTEGER"
                  examples:
                  - value: 2
                bodies:
                - type: "ARRAY"
                  items:
                    type: "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
                  examples:
                  - value: |-
                      [{
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Nourrir le poisson",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }]
              c0ae7d38-6d9a-44d1-9655-2e2cc441ad28:
                status: "400"
                description: "Statut 400"
                bodies:
                - type: "#/contract/types/2d2b154f-87f1-4433-a1c6-bd883ee7d9a7"
          f51853b9-831a-48d7-b6ad-64fead0e0e61:
            name: "Créer une tâche"
            method: "POST"
            securedBy:
            - scheme: "#/contract/securitySchemes/e95bce1c-b92c-4c6e-90b8-63c49689a29d"
              scopes: []
            bodies:
            - type: "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
              examples:
              - value: |-
                  {
                    "name": "Nourrir le poisson",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              "1ddf8be7-1079-413f-bb84-d4a223cb3a35":
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Nourrir le poisson",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
      "37bbd4ac-4055-4b68-b87e-42f4593cecaa":
        path: "/tasks/{taskid}"
        pathVariables:
        - name: "taskid"
          type: "STRING"
          description: "Identifiant de la tâche"
          examples:
          - value: "47ee3550-b619-11e6-8408-0bdb025a7cfa"
        operations:
          "9bc53bcb-5d33-4cd0-9f8e-2cd6430b3021":
            name: "Charger une tâche spécifique"
            method: "GET"
            responses:
              "0b46bd46-385f-4eef-8583-ee8222f00a40":
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Nourrir le poisson",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
              e1518b17-a4a2-4301-bb09-f1569ddf944b:
                status: "400"
                description: "Statut 400"
                bodies:
                - type: "#/contract/types/2d2b154f-87f1-4433-a1c6-bd883ee7d9a7"
          "70ba7cef-a4cd-474b-b67c-c6157dcbc05b":
            name: "Mettre une tâche à jour"
            method: "PUT"
            securedBy:
            - scheme: "#/contract/securitySchemes/e95bce1c-b92c-4c6e-90b8-63c49689a29d"
              scopes: []
            bodies:
            - type: "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
              examples:
              - value: |-
                  {
                    "name": "Nourrir le poisson",
                    "completed": false,
                    "createdAt": "2016.07.03"
                  }
            responses:
              a8a74827-f805-48d5-b6c0-fddfe88ecadf:
                status: "200"
                description: "Statut 200"
                bodies:
                - type: "#/contract/types/786d9250-95ca-4034-83bc-17db375c6d2f"
                  examples:
                  - value: |-
                      {
                        "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                        "name": "Nourrir le poisson",
                        "completed": false,
                        "createdAt": "2016.07.03"
                      }
          "37c5d283-3b29-4a8b-a1ea-f7dd2db08553":
            name: "Supprimer une tâche"
            method: "DELETE"
            securedBy:
            - scheme: "#/contract/securitySchemes/e95bce1c-b92c-4c6e-90b8-63c49689a29d"
              scopes: []
            responses:
              "92ba68e7-2ec2-4d0b-99dd-d84a7f335bf2":
                status: "200"
                description: "Statut 200"
    types:
      "786d9250-95ca-4034-83bc-17db375c6d2f":
        name: "Tâche"
        type: "OBJECT"
        description: "Un objet représentant une tâche."
        properties:
        - name: "id"
          type: "STRING"
          description: "Champ de clé primaire auto-généré"
          required: true
          examples:
          - value: "3fa2eb40-b61c-11e6-9de0-fdbe71bceebb"
        - name: "name"
          type: "STRING"
          required: true
          examples:
          - value: "Comprendre comment coloniser Mars"
        - name: "completed"
          type: "BOOLEAN"
          required: true
        - name: "createdAt"
          type: "STRING"
          examples:
          - value: "2016.10.06"
        examples:
        - value: |-
            {
              "id": "47ee3550-b619-11e6-8408-0bdb025a7cfa",
              "name": "Nourrir le poisson",
              "completed": false,
              "createdAt": "2016.07.03"
            }
      "2d2b154f-87f1-4433-a1c6-bd883ee7d9a7":
        name: "Erreur"
        type: "OBJECT"
        description: "Cette structure générale d'erreur est utilisée à travers toute l'API."
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
  components: {}
api-tryin: |-
  {
    "version" : 6,
    "entities" : [ {
      "entity" : {
        "type" : "Project",
        "name" : "API Tâches 4.1.0",
        "description" : "Une API pour gérer une liste de tâches à effectuer.",
        "importedFrom" : "9a416073-d9cc-4efb-8e39-9f7055180dcf"
      },
      "children" : [ {
        "entity" : {
          "type" : "Request",
          "id" : "ce9e46f7-f00e-4a19-be29-6468ceff67ca",
          "name" : "Charger la liste des tâches",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/",
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
                "value" : "createdAt DESC",
                "enabled" : false
              }, {
                "name" : "id",
                "value" : "47ee3550-b619-11e6-8408-0bdb025a7cfa",
                "enabled" : false
              }, {
                "name" : "name",
                "value" : "En savoir plus sur les API",
                "enabled" : false
              }, {
                "name" : "createdAt",
                "value" : "2016.07.03",
                "enabled" : false
              }, {
                "name" : "completed",
                "value" : "true",
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
          "id" : "f51853b9-831a-48d7-b6ad-64fead0e0e61",
          "name" : "Créer une tâche",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/"
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
            "textBody" : "{\n  \"name\": \"Nourrir le poisson\",\n  \"completed\": false,\n  \"createdAt\": \"2016.07.03\"\n}"
          }
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "9bc53bcb-5d33-4cd0-9f8e-2cd6430b3021",
          "name" : "Charger une tâche spécifique",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
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
          "id" : "70ba7cef-a4cd-474b-b67c-c6157dcbc05b",
          "name" : "Mettre une tâche à jour",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
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
            "textBody" : "{\n  \"name\": \"Nourrir le poisson\",\n  \"completed\": false,\n  \"createdAt\": \"2016.07.03\"\n}"
          }
        }
      }, {
        "entity" : {
          "type" : "Request",
          "id" : "37c5d283-3b29-4a8b-a1ea-f7dd2db08553",
          "name" : "Supprimer une tâche",
          "uri" : {
            "host" : "${\"BaseUrl\"}",
            "path" : "/tasks/{taskid}"
          },
          "method" : {
            "link" : "",
            "name" : "DELETE"
          },
          "headers" : [ ],
          "headersType" : "Form"
        }
      } ]
    } ],
    "environments" : [ {
      "name" : "API Tâches 4.1.0",
      "importedFrom" : {
        "projectId" : "9a416073-d9cc-4efb-8e39-9f7055180dcf"
      },
      "variables" : {
        "9d3844e9-1d30-41b0-b22f-e0fc34525455" : {
          "name" : "BaseUrl",
          "value" : "https://example.com",
          "enabled" : true,
          "private" : false
        }
      }
    } ]
  }
---
