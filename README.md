Docker_Cassandra_FastAPI

Este projeto consiste em criar um cluster Cassandra composto por 2 núcleos, em seguida criar uma API para testar a acessibilidade e o tempo de resposta da base de dados. Os dados representam os resultados da inspeção para restaurantes na cidade de Nova York.

A API é composta por 4 URLs que permitem o acesso a:

    para a informação de um restaurante a partir do seu id
    à lista de nomes de restaurantes do tipo de cozinha
    o número de inspeção de um restaurante de seu ID de restaurante
    os nomes dos 10 melhores restaurantes de uma determinada categoria

Criando o contêiner:

Para começar, crie o diretório pai e execute no terminal a partir deste diretório:

    git clone https://github.com/PaulSabia/Docker_Cassandra_FastAPI.git

Em seguida, execute o seguinte comando:

    docker-compose up --build

Preenchendo a base:

    docker cp db-schema/restaurants.csv cassandra-c01:/restaurants.csv

    docker cp db-schema/restaurants_inspections.csv cassandra-c01:/restaurants_inspections.csv

Em seguida, insira o contêiner para poder executar nossas consultas de criação de tabela CQL:

    docker exec -it cassandra-c01 cqlsh

Todas as solicitações de criação são agrupadas no arquivo init.cql
Última verificação:

Quando os dois containers Cassandra são criados, um ip específico é atribuído a eles. Aqui : 172.18.0.2e 172.18.0.3.

Para obter o ip (quando os containers estão rodando):

    docker exec -it cassandra-c01 nodetool status

No arquivo api.py, substitua os IPs na linha 10:

    cls.cluster = cluster.Cluster(['172.18.0.2', '172.18.0.3'], port=9042)

Teste de API:

Reinicie os contêineres: docker-compose up --buildentão vá para o seguinte endereço: http://localhost:8004/docs 