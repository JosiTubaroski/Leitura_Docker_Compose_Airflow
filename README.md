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

Define a imagem Docker para o Airflow e várias variáveis de ambiente necessárias para configuração do Airflow, incluindo a conexão com o banco de dados, backend Celery, configurações de servidor web, e-mail, etc.

#### 4. Volumes:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/04_Volumes.png">

Mapeia diretórios locais para os diretórios correspondentes dentro dos containers, garantindo que os dags, logs, plugins e dados persistam entre reinicializações dos containers.

#### 5. Usuário e Dependências:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/05_Usuarios_Dependencias.png">

Define o usuário que executará os containers e as dependências de serviços (Redis e PostgreSQL devem estar saudáveis antes de iniciar os serviços do Airflow).

### Serviços Definidos

#### 1. PostgreeSQL:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/06_Postgres_SQL.png">

Define o serviço PostegreSQL com as credenciais necessárias e um volume para persistir os dados do banco de dados. Também inclui um healthcheck para persistir os dados do banco de dados. Tambèm inclui um healthcheck para verificar se o banco está pronto.

#### 2. Redis:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/07_Redis.png">

Define o serviço Redis, expondo a porta 6379 e incluindo um healthcheck para garantir que o Redis está funcionando corretamente.

#### 3. Airflow Webserver:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/08_Airflow_Web.png">

Define o serviço de servidor web do Airflow, usando a configuração comum do Airflow, expondo a porta 8080, e verificando a saúde do serviço.

#### 4. Airflow Scheduler:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/09_Airflow_Scheduler.png">

Define o serviço de agendador do Airflow, responsável por orquestrar a execução dos DAGs.

#### 5. Airflow Worker:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/10_Airflow_Worker.png">

Define os trabalhadores Celery do Airflow, responsáveis por executar as tarefas agendadas.

#### 6. Airflow Triggerer:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/11_Airflow_Triggerer.png">

Define o serviço triggerer do Airflow, responsável por disparar tarefas baseadas em eventos.

#### 7. Airflow Init:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/12_Airflow_Init.png">

Serviço responsavel por inicializar o banco de dados do Airflow e criar o usuario web inicial.

#### 8. Airflow CLI:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/13_Airflow_CLI.png">

Serviço para executar comandos da linha de comando do Airflow.

#### 9. Flower:

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/14_Flower.png">

Serviço para monitoramento do Celery.

### Volumes

<img src="https://github.com/JosiTubaroski/Leitura_Docker_Compose_Airflow/blob/main/img/15_Volumes.png">

Define um volume Docker para persistir os dados do PostegreSQL.

Esse <b>'docker-compose.yml'</b> configura uma arquitetura completa para executar o Apache Airflow em um ambiente distribuído com PostgreSQL, Redis e vários serviços do Airflow. 





