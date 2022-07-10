# Entrega do teste de Java, API SigaBem

### :boy: Pessoal
* [Github](https://github.com/gabrielgua/sigabem-backend)
* [LinkedIn](https://www.linkedin.com/in/gabriel-guaitanele-niszczak-045102222/)
* gabriel.guaita45@gmail.com

### :link: Links úteis do projeto

* [Repositório do Projeto](https://github.com/gabrielgua/sigabem-backend)
* [Swagger](https://api-sigabem.herokuapp.com/swagger-ui/index.html)
* URL da API: (https://api-sigabem.herokuapp.com/)

## :desktop_computer: Tecnologias

* Java 11
* Spring Boot 2.7.1
* H2-database (test)
* Postgres (dev/prod)
* Swagger para documentação
* Heroku para Deploy
* Git para versionamento

## :pen: Métodos

* ### GET/frete
  Retorna uma lista dos Fretes salvos no banco.
  - #### Exemplo de request: 
  ```
    https://api-sigabem.herokuapp.com/frete
  ```

  - #### Exemplo de resposta: 

  ```
  [
    {
      "id": 1,
      "peso": 12,
      "cepOrigem": "83408538",
      "cepDestino": "60762835",
      "nomeDestinatario": "12345778",
      "vlTotalFrete": 12,
      "dataConsulta": "10/07/2022",
      "dataPrevistaEntrega": "20/07/2022"
    },
    {
      "id": 2,
      "peso": 23.5,
      "cepOrigem": "87035657",
      "cepDestino": "83606-472",
      "nomeDestinatario": "Romano",
      "vlTotalFrete": 5.88,
      "dataConsulta": "10/07/2022",
      "dataPrevistaEntrega": "11/07/2022"
    }
  ]
  ```

* ### GET/frete/{id}
  Retorna um Frete especificado pelo {id}.
  
  - #### Exemplo de request: 
  ```
  https://api-sigabem.herokuapp.com/frete/2
  ```

  - #### Exemplo de resposta: 

  ```
   {
     "id": 2,
     "peso": 23.5,
     "cepOrigem": "87035657",
     "cepDestino": "83606-472",
     "nomeDestinatario": "Romano",
     "vlTotalFrete": 5.88,
     "dataConsulta": "10/07/2022",
     "dataPrevistaEntrega": "11/07/2022"
   }
  ```

* ### POST/frete
  Faz uma consulta do valor total do Frete, Data Prevista de Entrega e Salva o Frete no banco de dados.
  
  - #### Exemplo de request: 
  ```
  https://api-sigabem.herokuapp.com/frete
  ```

  - #### Exemplo de Input: 
  ```
  { 
    "peso": 25.5,
    "cepOrigem": "87035-657",
    "cepDestino": "83606-472",
    "nomeDestinatario": "Romano",
  }
  ```

  - #### Exemplo de resposta: 
  ```
  {
    "id": null,
    "vlTotalFrete": 5.875,
    "cepOrigem": "87035-657",
    "cepDestino": "83606-472",
    "dataPrevistaEntrega": "11/07/2022"
  }
  ```

  - #### Frete salvo no Banco:
  ```
  {
    "id": 2,
    "peso": 23.5,
    "cepOrigem": "87035-657",
    "cepDestino": "83606-472",
    "nomeDestinatario": "Romano",
    "vlTotalFrete": 5.88,
    "dataConsulta": "10/07/2022",
    "dataPrevistaEntrega": "11/07/2022"
  }
  ```

## :exclamation: Exception Handling

* ### Validação dos campos

  - #### Exemplo de request: 
  ```
  https://api-sigabem.herokuapp.com/frete
  ```

  - #### Exemplo de input: 
  ```
  {
    "peso": 12,
    "cepOrigem": "83408538" 
  }
  ```

  - #### Exemplo de resposta: 
  ```
  {
    "timestamp": 1657493832944,
    "status": 400,
    "error": "Validation Error",
    "message": "Erro na validação dos campos",
    "path": "/frete",
    "errors": [
        {
          "fieldName": "nomeDestinatario",
          "message": "Nome do Destinatário é requerido!"
        },
        {
          "fieldName": "cepDestino",
          "message": "Cep de Destino é requerido!"
        }
    ]
  }
  ```

* ### Objeto Não encontrado

  - #### Exemplo de request: 
  ```
  https://api-sigabem.herokuapp.com/frete/5
  ```

  - #### Exemplo de resposta: 

  ```
  {
    "timestamp": 1657494034826,
    "status": 400,
    "error": "Object not Found",
    "message": "Frete não encontrado, id: 5",
    "path": "/frete/5"
  }
  ```










