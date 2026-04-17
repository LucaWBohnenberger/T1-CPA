# Como executar o notebook

Este projeto usa um ambiente criado com conda.
Ele reúne notebooks de apoio para atividades da disciplina, com foco em análise e experimentação de dados.
As principais libs utilizadas são foram selenium e requests.
O ambiente foi preparado para facilitar a execução dos exercícios de forma reproduzível.

## 1. Criar o ambiente a partir do arquivo `environment.yml`

```bash
conda env create -f environment.yml
```

## 2. Ativar o ambiente

```bash
conda activate cpaT12
```

## 3. Abrir o notebook

Na pasta do projeto, execute:

```bash
jupyter notebook
```

Ou use alguma IDE que suporte notebooks, como o VSCode.
