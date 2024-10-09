# DESCRIÇÃO
A Nuvem da AWS nos trás tecnologias para diversas industrias e campos. Uma que vem me chamando atenção é a area de dados, especialmente a de Engenharia de dados. Entre os serviços que se destacam temos o [AWS Glue](https://aws.amazon.com/pt/glue/). Ele é um serviço de integração de dados sem servidor, que torna possivel a preparação de dados de forma simples, pratica e barata em qualquer escala. Com ele é possivelconectar-se a mais de 70 fontes diferentes de dados, visualização, contrução e monitoramento de pipelines de [ETL](https://aws.amazon.com/pt/what-is/etl/).

Este projeto foi feito com o intuito de ajudar a exercitar fundamentos de Engenharia de dados utilizando-se dos serviços de engenharia de dados da nuvem da AWS. Nele foi contruido uma pipeline basica de ETL com ultilizando S3 para simular nosso armazenamento na [staging layer](https://kb.ufla.br/books/termos-e-definicoes-governanca-de-dados/page/staging-area)  e nossa [data warehouse](https://aws.amazon.com/pt/what-is/data-warehouse/). Glue construirá nossa pipeline e utilizaremos o mesmo para criar um [Glue Crawler](https://docs.aws.amazon.com/pt_br/glue/latest/dg/add-crawler.html) para popular um banco de dados no [Glue Catalog](https://docs.aws.amazon.com/pt_br/glue/latest/dg/start-data-catalog.html).
Posteriormente iremos usar o [AWS Athena](https://aws.amazon.com/pt/athena/) para realizar [Querys SQL](https://aws.amazon.com/pt/what-is/sql/) no nosso banco de dados do Glue Catalog. Por fim usaremos o [QuickSight](https://aws.amazon.com/pt/quicksight/) para construir visualizações dos nossos dados.
Como sempre estarei providenciando imagens para ajudar na compreender melhor cada passo e links utéis da documentação para ajudar a compreensão dos conceitos abordados.

# Arquitetura
![diagrama](./img/diagram.png)

# Technologias ultilizadas
- AWS Glue
- S3
- AWS Athena
- Amazon QuickSight

# Dataset
O Dataset utilizado trata-se do [Spotify Dataset 2023](https://www.kaggle.com/datasets/tonygordonjr/spotify-dataset-2023) hospedado no [Kaggle](https://www.kaggle.com/), ele é um dataset bem rico que consiste de 5 arquivos CSV. Nele vamos encontrar dados sobre musicas(track), artistas(artists) e albums(albums). Os dados são brutos logo será necessario pre-processa-los para utiliza-lo. Neste repositorio deixarem os dados preprocessados para facilitar a replicabilidade do projeto. Nossos dados preprocessados consistem em 3 CSV files com nomes de albums, artits e track.

# S3 Staging Layer e Data warehouse
O primeiro passo a se fazer neste projeto é criar nosso sistema de armazenamento que simulara nossa area de staging e nossa data warehouse. Para isso vamos usar o Amazon S3.

![s31](./imag/s3/s31.png)

Aqui criamos um Bucket S3 com nome de *data-eng-spotfiy* e no mesmo vamos criar duas pastas uma que será nossa Stanging layer com nome *staging* e ou que sera nossa Data Warehouse com nome de *datawarehouse*.
