# Relatório de Desenvolvimento: Laboratório 1 - Web Scraping

**Disciplina:** Coleta, Preparação e Análise de Dados  
**Professora:** Katherine Bianchini Esper  
**Aluno:** Luca Wolffenbüttel Bohnenberger

---

## 1. Introdução

Este relatório descreve o desenvolvimento do Laboratório 1, cujo objetivo foi aplicar técnicas de web scraping em um ambiente controlado: a exploração de conexões na Wikipédia. O documento detalha a lógica utilizada, os desafios encontrados durante a extração e a análise dos dados obtidos.

---

## 2. Lógica Utilizada e Desenvolvimento

### Ambiente Controlado (Wikipédia)

Para a tarefa, o artigo inicial escolhido foi o do matemático **Andrey Kolmogorov**. O crawler foi desenvolvido em Python, utilizando as bibliotecas **requests** para as requisições HTTP e **BeautifulSoup** para a conversão e navegação na árvore DOM do HTML.

#### Navegação e Extração

A partir da página inicial, o script:

- Localiza o título (tag `h1`).
- Captura todas as tags `img` (convertendo URLs relativas em absolutas via `urljoin`).
- Filtra os links internos garantindo que comecem com `/wiki/` e não contenham `:` (para evitar páginas administrativas).

#### Exportação

Os dados foram armazenados localmente:

- Os arquivos HTML brutos foram salvos em uma pasta dedicada.
- As informações estruturadas foram exportadas para dois arquivos CSV distintos (`images.csv` e `arquivo.csv`), ambos contendo uma coluna de **timestamp** com o momento exato da coleta.

---

## 3. Dificuldades Encontradas e Soluções

### Inconsistências na Wikipédia

Durante o desenvolvimento, a principal dificuldade foi lidar com as inconsistências na organização dos parágrafos (`<p>`) na Wikipédia. Observou-se que a estrutura do HTML variava: em alguns casos, o primeiro parágrafo estava corretamente na primeira tag `<p>`, enquanto em outros, a tag continha apenas espaços, quebras de linha, caracteres aleatórios ou elementos invisíveis e de formatação antes do texto real.

#### Solução

Para contornar isso, foi implementada uma iteração sobre todos os parágrafos dentro da `div bodyContent`. Foi adicionada uma regra simples para verificar se o parágrafo estava vazio ou continha apenas espaços, juntamente com uma heurística de comprimento: o algoritmo assegura que o conteúdo do parágrafo tenha um tamanho mínimo (mais de 5 caracteres). Essa abordagem filtrou conteúdos vazios ou irrelevantes, garantindo que a extração considerasse apenas o primeiro bloco de texto genuíno do artigo.

---

## 4. Análise dos Resultados Obtidos

A execução demonstrou a densidade da rede de links da Wikipédia. Apenas na página inicial de Kolmogorov, o crawler identificou centenas de ramificações válidas para outros artigos. Os CSVs gerados mantiveram a integridade das URLs absolutas e o registro temporal, validando o sucesso da estrutura de salvamento.

---

## 5. Conclusão

O desenvolvimento deste laboratório permitiu consolidar os conceitos de coleta de dados não estruturados. Apesar das dificuldades iniciais com a formatação HTML variável da Wikipédia, as estratégias adotadas garantiram a extração limpa e a estruturação correta dos dados nos formatos CSV exigidos.