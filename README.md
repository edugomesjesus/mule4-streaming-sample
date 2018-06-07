# mule4-streaming-sample

Este sample demonstra o processo assíncrono de escrita em um arquivo no sistema de arquivos percorrendo os itens de uma lista JSON enviada via POST. O arquivo criado extrai o campo **email** dos elementos iterando sobre deles com o uso do __dataweave 2.0__.
Em seguida, para cada iten processado que possue o elemento **order** é criado um novo aquivo .csv no sistema de arquivos, caso contrário uma mensagem é impressa no console.

This demonstrates calling HTTP URL to get JSON data and extract content out of nested JSON for logging purpose to answer this question - https://forums.mulesoft.com/questions/92885/extract-value-from-nested-json-object-mule-4.html

Demonstração dos seguintes novos recursos do Mule 4: 
 - Streaming;
 - Acesso direto aos dados: Não é mais necessário transformar os dados em um formato específico para manipulação, isto é feito automaticamente;
 - DataWeave: expressões do dataweave incorporado nos conectores para manipulação da estrutura dos dados de entrada.

Esse sample considerou as seguintes versões:
 - Anypoint Studio 7.1.3
 - Mule Server Runtime 4.1.1

Para executar esse sample a seguinte requisição HTTP foi utilizada:

```curl
curl -X POST \
  http://127.0.0.1:9090/ \
  -H 'Content-Type: application/json' \
  -d '{
    "customers": [
        {
            "order": "179",
            "firstName": "Walter",
            "lastName": "Doe",
            "email": "t79@email.com",
            "gender": "Male",
            "address": "220.17.245.127.51231241"
        },
        {
            "order": "180",
            "firstName": "João",
            "lastName": "Silva",
            "email": "t80@email.com",
            "gender": "Male",
            "address": "220.17.245.127.51231241"
        },
        {
            "order": "181",
            "firstName": "Maria",
            "lastName": "Santos",
            "email": "t81@email.com",
            "gender": "Male",
            "address": "220.17.245.127.51231241"
        },
        {
            "firstName": "Cabral",
            "lastName": "Nascimento",
            "email": "t82@email.com",
            "gender": "Male",
            "address": "220.17.245.127.51231241"
        }
    ]
}'
```