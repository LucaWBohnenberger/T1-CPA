# Laboratório 1: Web Scraping

Este repositório contém a resolução do *T1* da disciplina de Coleta, Preparação e Análise de Dados da PUCRS. O projeto tem como objetivo aplicar técnicas de extração de dados em no cenário de exploração de conexões em um ambiente controlado (Wikipédia).

## Tecnologias Utilizadas

- Python 3.10.19  
- BeautifulSoup4  
- Requests  
- Jupyter Notebook  

## Como Executar o Projeto

Para garantir que o código rode perfeitamente e sem conflitos de versão, utilizamos o **Conda** para isolar o ambiente de desenvolvimento. Siga os passos abaixo para preparar a sua máquina:

### 1. Criar o Ambiente Virtual

Abra o seu terminal (ou Anaconda Prompt) na pasta raiz do projeto e crie um ambiente especificando a versão exata do Python:

```bash
conda create --name lab_scraping python=3.10.19 -y
```

### 2. Ativar o Ambiente

Ative o ambiente criado:

```bash
conda activate lab_scraping
```

### 3. Instalar as Dependências

Com o ambiente ativado, instale todas as bibliotecas necessárias que estão listadas no arquivo `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 4. Executar os Arquivos

Se você for rodar os arquivos `.ipynb`, inicie o Jupyter:

```bash
jupyter notebook
```

Certifique-se de selecionar o kernel `lab_scraping` no canto superior direito do seu notebook.


## Estrutura de Entrega

- `/html` → Arquivos HTML brutos baixados da Wikipédia  
- `/csvs` → Dados estruturados e links extraídos  
- `requirements.txt` → Lista de dependências do projeto  
- `Relatorio.pdf` → Explicação da lógica, dificuldades e análise dos resultados  

## Desenvolvido por

Luca W.B
