# Previsão de Eventos em Partidas de Futebol com Modelos de Linguagem de Grande Escala

Este repositório contém o código e materiais utilizados em um projeto de pesquisa que faz parte do [**MBA em Ciência de Dados do ICMC/USP**](https://cemeai.icmc.usp.br/MBA/) 

O objetivo é investigar a aplicação de **Modelos de Linguagem de Grande Escala (LLMs)** na previsão de eventos em partidas de futebol[

---

## Visão Geral

O projeto explora a etapa de **fine-tuning** de modelos como GPT-2, DistilGPT-2, GPT-Neo-125M e OPT-125M, com foco na **previsão de ações futuras** a partir de sequências de eventos em jogos de futebol.

Banco de dados: [StatsBomb 360](https://statsbomb.com/what-we-do/soccer-data/360-2/).

O trabalho envolve:

1. **Coleta e análise de dados** (StatsBomb 360)
2. **Manipulação e formatação** dos eventos para gerar sequências de lances
3. **Tokenização** e preparação do dataset
4. **Treinamento e avaliação** dos modelos
5. **Aplicação** dos modelos treinados para geração de previsões (texto/eventos)

---

## Estrutura do Repositório

- **`codes/`**  
  - `1_DataExplore.ipynb` – Notebook para explorar os dados do StatsBomb 360  
  - `2_DataManipulation.ipynb` – Manipular os dados e construir as sequências de eventos  
  - `3_Tokenizer.ipynb` – Código para tokenizar o dataset  
  - `4_Training.ipynb` – Treinamento de um modelo LLM com fine-tuning  
  - `5_Training_AllModels.ipynb` – Código otimizado para treinar e comparar diferentes modelos  
  - `06_UseModels.ipynb` – Notebook para carregar os modelos treinados, gerar previsões (eventos e texto)  

- **`materias/`**  
  - Pasta contendo artigos científicos e materiais de referência utilizados no projeto.  

---

## Datasets, Tokenizers e Modelos Fine-Tuning no Hugging Face

A pesquisa gerou diversos **datasets** de sequências de eventos e **tokenizers** específicos, bem como **checkpoints de modelos LLM** fine-tuninh.

Todos os datasets, tokenizers e modelos estão disponíveis na conda do hugging face: [huggingface.co/murloms](https://huggingface.co/muriloms)

A seguir, listamos os principais repositórios disponíveis no Hugging Face:

### Datasets

- **Sequências de 3 lances (5.000 sequências)**  
  - [`muriloms/football-events-statsbomb360-la-liga-3-5k`](https://huggingface.co/datasets/muriloms/football-events-statsbomb360-la-liga-3-5k)

- **(Exemplo de ampliação)**: Para cada variação (3, 5, 10, 40 eventos de histórico) e (5.000, 10.000, 50.000 sequências), foram criados datasets correspondentes:
  - `muriloms/football-events-statsbomb360-la-liga-3-10k`
  - `muriloms/football-events-statsbomb360-la-liga-3-50k`
  - `muriloms/football-events-statsbomb360-la-liga-5-5k`
  - `muriloms/football-events-statsbomb360-la-liga-5-10k`
  - `muriloms/football-events-statsbomb360-la-liga-5-50k`
  - `muriloms/football-events-statsbomb360-la-liga-10-5k`
  - ...

### Tokenizers

- **Tokenizer de 3 eventos e 5.000 sequências (GPT-2)**  
  - [`muriloms/tcc-football-events-tokenizer-gpt2-3-5k`](https://huggingface.co/muriloms/tcc-football-events-tokenizer-gpt2-3-5k)  

- **(Exemplo para outras configurações)**:
  - `muriloms/tcc-football-events-tokenizer-gpt2-10-10k`
  - `muriloms/tcc-football-events-tokenizer-distilgpt2-3-5k`
  - `muriloms/tcc-football-events-tokenizer-gptneo-40-50k`
  - ...

### Modelos Fine-Tuning

- **GPT-2 finetunado (3 lances e 5.000 sequências, 100 epochs)**  
  - [`muriloms/tcc-football-events-finetune-gpt2-3-5k-100`](https://huggingface.co/muriloms/tcc-football-events-finetune-gpt2-3-5k-100)

- **(Exemplo para outras configurações)**:
  - `muriloms/tcc-football-events-finetune-distilgpt2-3-5k-100`
  - `muriloms/tcc-football-events-finetune-gptneo-125m-5-10k-100`
  - `muriloms/tcc-football-events-finetune-opt-125m-3-5k-100`
  - ...

---

## Modelos Originais Utilizados

1. [GPT-2](https://huggingface.co/openai-community/gpt2)  
2. [DistilGPT-2](https://huggingface.co/distilbert/distilgpt2)  
3. [GPT-Neo-125M](https://huggingface.co/EleutherAI/gpt-neo-125m)  
4. [OPT-125M](https://huggingface.co/facebook/opt-125m)  

Esses modelos foram escolhidos por oferecerem diferentes tamanhos (quantidade de parâmetros) e arquiteturas, possibilitando comparar desempenho, custo computacional e viabilidade de uso em cenários de previsão de eventos esportivos.

---
