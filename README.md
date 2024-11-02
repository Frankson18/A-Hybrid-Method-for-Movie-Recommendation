# A-Hybrid-Method-for-Movie-Recommendation
Este repositório contém o código para implementar um sistema de recomendação híbrido de filmes, que combina **clusterização com K-Means** e **Decomposição em Valores Singulares (SVD)**. A abordagem híbrida utiliza tanto filtragem baseada em conteúdo quanto filtragem colaborativa para entregar recomendações mais personalizadas e precisas, abordando desafios como o *cold start* e a superespecialização.

## Sumário
- [Introdução](#introdução)
- [Metodologia](#metodologia)
  - [Conjunto de Dados](#conjunto-de-dados)
  - [Pré-processamento dos Dados](#pré-processamento-dos-dados)
  - [Filtragem Baseada em Conteúdo com K-Means](#filtragem-baseada-em-conteúdo-com-k-means)
  - [Filtragem Colaborativa com SVD](#filtragem-colaborativa-com-svd)
  - [Implementação do Modelo Híbrido](#implementação-do-modelo-híbrido)
- [Resultados](#resultados)
- [Trabalhos Futuros](#trabalhos-futuros)
- [Referências](#referências)

## Introdução
Sistemas de recomendação são ferramentas essenciais em várias indústrias, especialmente no setor de entretenimento, onde ajudam os usuários a descobrir novos conteúdos. Métodos tradicionais, como **filtragem colaborativa** e **filtragem baseada em conteúdo**, têm suas vantagens e limitações. Este projeto visa aumentar a precisão das recomendações ao combinar essas duas técnicas em um modelo híbrido, minimizando problemas como a escassez de dados (*cold start*) e a especialização excessiva.

## Metodologia
Este projeto utiliza o [Conjunto de Dados MovieLens Completo](https://grouplens.org/datasets/movielens/), que contém aproximadamente 45 mil filmes e 26 milhões de avaliações de 270 mil usuários, fornecendo uma base robusta para a construção e teste do modelo de recomendação.

### Conjunto de Dados
- **movies_metadata.csv**: Metadados para cada filme, incluindo título, gêneros e resumos.
- **keywords.csv**: Palavras-chave associadas aos enredos dos filmes.
- **ratings.csv**: Avaliações de usuários para vários filmes.

### Pré-processamento dos Dados
O pré-processamento inclui:
1. Seleção das colunas relevantes.
2. Conversão de campos de dados em formato JSON (ex.: gêneros, palavras-chave).
3. Mesclagem dos conjuntos de dados e limpeza dos dados.
4. Aplicação do vetor de características TF-IDF e stemming para criar uma matriz de características para a clusterização.

### Filtragem Baseada em Conteúdo com K-Means
Utilizando o K-Means, os filmes são agrupados em clusters com características similares. A quantidade ideal de clusters é determinada por meio do **Erro Quadrático Médio (WCSS)** e do **Índice de Silhueta**.

### Filtragem Colaborativa com SVD
O SVD é aplicado na matriz de avaliações de usuário-filme para prever avaliações potenciais para cada usuário. Essa técnica é particularmente eficaz para a filtragem colaborativa, pois identifica fatores latentes que capturam as preferências dos usuários.

### Implementação do Modelo Híbrido
O sistema híbrido de recomendação integra o K-Means e o SVD da seguinte maneira:
1. **Filtragem Baseada em Conteúdo**: Gera um conjunto inicial de recomendações com base na similaridade entre filmes.
2. **Filtragem Colaborativa**: Refina as recomendações utilizando dados de avaliações de usuários, garantindo sugestões mais personalizadas e precisas.

## Resultados
A abordagem híbrida aprimora a qualidade das recomendações ao combinar a filtragem baseada em conteúdo, orientada por clusters, com a filtragem colaborativa. Os resultados experimentais indicam um desempenho consistente em diferentes divisões de validação, com valores baixos de RMSE e MAE, demonstrando a confiabilidade do modelo.

## Trabalhos Futuros
Melhorias adicionais podem incluir a experimentação com outros algoritmos de clusterização, como **Two Towers** e **Modelos de Mistura Gaussiana (GMM)**, bem como a expansão do modelo para outros domínios, como recomendações de músicas e produtos de e-commerce.

## Referências
Para mais informações sobre a metodologia, resultados e fundamentação teórica, consulte:
- Burke, R. (2002). *Hybrid recommender systems: Survey and experiments.*
- Koren, Y., Bell, R., & Volinsky, C. (2009). *Matrix factorization techniques for recommender systems.*
- Outras referências disponíveis no artigo.
