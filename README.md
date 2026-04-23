# Estudo de Caso: O Problema da Entrega Inteligente (FastBite) 

Este repositório contém a análise técnica e a proposta de solução para o desafio logístico da plataforma **FastBite**, desenvolvido para a unidade curricular de Estruturas de Dados e Análise de Algoritmos.

##  Visão Geral do Problema
O estudo de caso da FastBite descreve um desafio de otimização logística: organizar a atribuição e o roteamento de entregas em um ambiente de alta demanda. 
* **Volume:** O sistema precisa processar 80.000 pedidos por dia.
* **Janela de Decisão:** As decisões de rota devem ser tomadas em no máximo 2 segundos, para não comprometer a operação.
* **Objetivo:** Definir qual entregador ficará com cada pedido e a sequência de coletas e entregas que minimize o tempo total, respeitando restrições como capacidade máxima de 3 pedidos por entregador e janelas de tempo para pedidos urgentes.

##  Análise Técnica
Tecnicamente, trata-se de um problema **NP‑Completo**, pois reúne características do Caixeiro Viajante (TSP) e do Roteamento de Veículos (VRP). 

* **Inviabilidade de Força Bruta:** É impossível buscar a solução ótima por força bruta, já que as combinações crescem exponencialmente conforme novos pedidos entram no sistema. 
* **Escalabilidade:** Com apenas 50 pedidos e 20 entregadores, a enumeração exaustiva de todas as possibilidades já foge do alcance prático dentro do limite de tempo disponível.

##  Avaliação de Estratégias Algorítmicas
O documento avalia várias estratégias para enfrentar esse cenário:

1. **Métodos Gulosos:** São rápidos e tomam decisões locais imediatas (como escolher o ponto mais próximo), mas podem levar a rotas subótimas por não anteciparem efeitos futuros.
2. **Programação Dinâmica:** Pode otimizar a rota de um entregador individualmente, porém exige muita memória e tempo à medida que o número de paradas cresce.
3. **Divisão e Conquista:** Segmenta a cidade em zonas para facilitar o processamento, mas complica o tratamento de entregas que atravessam fronteiras entre setores.

##  Solução de Engenharia Real
Na prática, a solução adotada pela FastBite prioriza **heurísticas eficientes** em vez de perfeição matemática. A proposta de engenharia consiste em:

* **Particionamento Geográfico:** Organização inicial por regiões.
* **Geração de Soluções Iniciais:** Uso de algoritmos rápidos para uma resposta imediata.
* **Refinamentos Locais:** Melhoria das rotas em tempo real conforme o processamento permite.

Essa abordagem busca um equilíbrio entre qualidade do serviço e viabilidade computacional, entregando respostas suficientemente boas dentro do limite de 2 segundos exigido pela operação.

---
**Professor:** Alexandre "Montanha" de Oliveira  
**Unidade Curricular:** Estruturas de Dados e Análise de Algoritmos
