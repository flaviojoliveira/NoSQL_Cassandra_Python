# NoSQL_Cassandra_Python
Projeto executado na disciplina de POO II - Talis
frasco-cassandra
Python Flask Cassandra Simple Shop CRUD

Esta é uma coleção de aplicativo Cassandra Shop simples e ilustrativo. O objetivo desta coleção é ajudar os novos usuários do Cassandra a entender melhor o Cassandra e apresentar casos de uso ilustrativos.
Começando

Se você não tiver acesso a um cluster do Cassandra, poderá começar instalando com o HomeBrew para Mac.
Começando

Se você já tiver acesso a um cluster do Cassandra, poderá começar a executar este aplicativo de exemplo imediatamente. Tudo o que você precisa fazer é definir uma variável de ambiente em seu cliente indicando onde seu cluster está localizado:

   $ export BACKEND_STORAGE_IP='mycluster_ip'

No entanto, se você não tiver acesso a um cluster do Cassandra, poderá começar instalando o Ferry . Ferry é uma ferramenta de código aberto que ajuda os desenvolvedores a provisionar clusters virtuais em uma máquina local. O Ferry suporta Cassandra (e outras ferramentas de "big data") e não requer que você realmente saiba como configurar o Cassandra para começar.

Supondo que você esteja usando o Ferry, você deve executar todos esses comandos em um cliente Cassandra. A primeira coisa a fazer é instalar todos os pacotes de pré-requisitos. Eles podem ser encontrados em requirements.txt. Aqui está uma maneira simples de fazer isso a partir da linha de comando usando pip.

   $ pip install -r requirements.txt

Depois, você desejará configurar o keyspace do Cassandra para nosso aplicativo.

   $ cqlsh -f createtable.cql

Depois de criar a tabela, você poderá iniciar o servidor web digitando:

   $ python app.py runserver

Depois, insira alguns dados no Cassandra digitando:

   $ python rest-client.py post

Então, vamos ver quais dados foram inseridos.

   $ python rest-client.py fetch  

Além disso, vamos atualizar quais dados foram inseridos.

   $ python rest-client.py update  

Por fim, vamos excluir os dados que foram inseridos.

   $ python rest-client.py delete  
