# Laboratório 1: Web Scraping - IMDb Top 250

## Informações do Projeto
* **Disciplina:** Coleta, Preparação e Análise de Dados
* **Professora:** Katherine Bianchini Esper
* **Data de Entrega:** 10/04/2026
* **Tecnologias Utilizadas:** Python, Selenium, XPath e JSON.

## Objetivo da Tarefa
Realizar o scraping do site [IMDb](https://www.imdb.com/pt/) para capturar:
1.  A listagem dos 250 filmes com maiores avaliações.
2.  Detalhes específicos de cada filme: Título, ano de lançamento, nota, gêneros, diretores e o pôster (URL e download da imagem).
3.  Exportação dos dados consolidados para um arquivo JSON.

## Desafios e Soluções (Relatório de Desenvolvimento)

Durante o desenvolvimento, foram enfrentados obstáculos técnicos significativos que exigiram adaptações na lógica de coleta:

### 1. Inconsistência de Classes e Selenium Puro
A estrutura de classes do IMDb mostrou-se altamente instável e inconsistente entre diferentes filmes. Inicialmente, tentou-se utilizar apenas localizadores de classe via Selenium puro, porém essa abordagem falhou ao tentar localizar os **diretores**.
* **Solução:** Foi necessário migrar a estratégia para o uso de **XPath**, que se mostrou muito mais resiliente para navegar na árvore do DOM e encontrar os elementos de direção de forma assertiva.

### 2. Tratamento de Metadados (Ano, Idade e Duração)
As informações de ano, classificação indicativa e duração do filme são apresentadas em uma linha de metadados que se comporta como uma tupla de até 3 itens. Contudo, nem todos os filmes possuem classificação indicativa (idade mínima).
* **Dificuldade:** Em alguns filmes, a ordem ou a presença desses itens variava, o que quebrava a extração indexada simples.
* **Solução:** Implementação de uma lógica condicional (`if/else`) para verificar o conteúdo de cada posição da lista, garantindo que o ano e a duração fossem atribuídos corretamente mesmo na ausência da idade mínima.

### 3. O Ciclo de Vida das Imagens (URLs vs. Visualizações)
Um ponto crítico ocorreu na etapa de download dos pôsteres. Originalmente, as URLs capturadas não eram links diretos para os arquivos de imagem (`.jpg`), mas sim links para a página de **visualização** do IMDb (uma interface HTML com a imagem dentro).
* **Refatoração:** Foi necessário criar uma célula de processamento dedicada para:
    1.  Identificar as URLs de visualização.
    2.  Extrair a URL real do recurso de imagem dentro dessas páginas.
    3.  Atualizar a base de dados com as URLs de imagem de fato.
    4.  Realizar o download físico das imagens para o diretório local.


### 4. Tamanho de Imagens
Por conta do tamanho de imagens, removi a pasta de posters do repositorio, pois se não o arquivo ficaria grande de mais para enviar pelo moodle. O código para baixar as imagens continua presente, mas os arquivos em si não estão mais no repositório.
