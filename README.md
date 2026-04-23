# Estudo de Caso: O Problema da Entrega Inteligente (FastBite) 🚀

Este repositório contém a análise técnica e a proposta de solução para o desafio logístico da plataforma **FastBite**, desenvolvido para a unidade curricular de Estruturas de Dados e Análise de Algoritmos.

## 📋 Visão Geral do Problema
A FastBite enfrenta um desafio de otimização logística em larga escala:
* [cite_start]**Volume:** +80.000 pedidos/dia[cite: 9].
* [cite_start]**Janela de Decisão:** Máximo de 2 segundos de processamento[cite: 31, 32].
* [cite_start]**Objetivo:** Minimizar o tempo total de entrega, otimizando a atribuição de entregadores e o roteamento das coletas/entregas[cite: 38].

---

## 🛠️ Análise Técnica

### 1. Classificação de Complexidade
[cite_start]O problema é classificado como **NP-Completo**[cite: 52, 57]. Ele combina dois problemas clássicos da computação:
* [cite_start]**TSP (Traveling Salesman Problem):** Roteamento otimizado de um único agente[cite: 46].
* [cite_start]**VRP (Vehicle Routing Problem):** Gestão de múltiplos veículos com restrições de capacidade e tempo[cite: 47].

> [cite_start]**Nota:** A solução por força bruta é inviável, pois o espaço de soluções cresce de forma explosiva (fatorial), tornando impossível a avaliação exaustiva em tempo real[cite: 42, 62].

### 2. Estratégias Algorítmicas Avaliadas

* [cite_start]**Abordagem Gulosa (Greedy):** Foca em escolhas locais imediatas (ex: ir ao ponto mais próximo)[cite: 71, 74]. [cite_start]É extremamente rápida, mas pode gerar rotas subótimas por não considerar o impacto global das decisões[cite: 75].
* [cite_start]**Programação Dinâmica (PD):** Aplicável para otimizar a rota individual de um entregador[cite: 79, 80]. [cite_start]No entanto, possui alto custo de memória e tempo, tornando-se impraticável conforme o número de pedidos por entregador aumenta[cite: 82, 83].
* [cite_start]**Divisão e Conquista:** Baseia-se na segmentação da cidade em zonas geográficas[cite: 86]. [cite_start]Embora facilite o processamento, apresenta dificuldades críticas na gestão de pedidos que cruzam as fronteiras entre setores[cite: 88].

---

## 💡 Proposta de Solução: Engenharia Real

[cite_start]Para atender aos requisitos de produção, a solução proposta foca em **Heurísticas** — técnicas que entregam soluções "suficientemente boas" dentro do limite de tempo[cite: 95, 96].

### Arquitetura da Solução:
1.  [cite_start]**Particionamento Geográfico:** Divisão inicial dos pedidos por região para reduzir a complexidade[cite: 100].
2.  [cite_start]**Heurística Gulosa Inicial:** Geração imediata de uma rota base viável[cite: 101].
3.  [cite_start]**Refinamento Local:** Aplicação de algoritmos de troca (ex: troca de pedidos entre entregadores) para otimização contínua[cite: 102].
4.  [cite_start]**Time-boxing:** Interrupção forçada do processamento aos 2 segundos para garantir a resposta em tempo real[cite: 103].

---

## 🎓 Identificação
* [cite_start]**Disciplina:** Estruturas de Dados e Análise de Algoritmos (0006963) [cite: 4]
* [cite_start]**Professor:** Alexandre "Montanha" de Oliveira [cite: 4]
* [cite_start]**Nível:** Graduação - Preparatório A1 [cite: 5]

---
> [cite_start]*"A ciência da computação não é sobre computadores tanto quanto a astronomia não é sobre telescópios."* — Edsger W. Dijkstra [cite: 162, 163]
