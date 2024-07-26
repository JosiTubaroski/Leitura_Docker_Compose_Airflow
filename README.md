# Leitura Docker Compose Airflow

O <b>'docker-compose.yml'</b> fornecido define um conjunto de serviços para executar Apache Airflow com um executor Celery, usando PostegreSQL como banco de dados e Redis como backend
de mensagens. Aqui está uma análise passo a passo do que está sendo feito:

### Estrutura Comum

#### 1. Versão:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/01_Versao.png">

Define a versão do arquivo de configuração do Docker Compose.


#### 2. x-airflow-common:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/02_X_Common.png">

Define uma âncora chamada 'airflow-common' que será usada para compartilhar configurações comuns entre vários serviços do Airflow.

### Configurações Comuns do Airflow

#### 3. Imagem e Ambiente:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/03_Imagens_Ambiente.png">

