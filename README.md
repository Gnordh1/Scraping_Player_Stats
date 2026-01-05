# ⚽ Soccer Scouting Data Pipeline: FBRef & Transfermarkt

Este repositório contém um pipeline completo em Python para coleta, tratamento e consolidação de dados de jogadores de futebol, integrando estatísticas de performance (FBRef) com perfis físicos e de mercado (Transfermarkt).

O objetivo é automatizar a criação de uma base de dados robusta para análise de **Scouting e Recrutamento**.

## 🚀 Funcionalidades

O projeto é dividido em quatro etapas principais dentro do notebook:

1.  **Scraping FBRef (Performance):** Captura métricas detalhadas (finalizações, passes, defesa, posse, etc.) de todos os jogadores de uma liga específica, utilizando `cloudscraper` para contornar bloqueios de acesso.
2.  **Scraping Transfermarkt (Perfil):** Identifica automaticamente todos os clubes de uma liga e extrai dados de altura, pé preferencial e valor de mercado de cada atleta.
3.  **Normalização e Fusão:** Limpa nomes (remoção de acentos/especiais) e une as duas fontes de dados através de uma chave única (Nome + Ano de Nascimento).
4.  **Data Cleaning Final:** Padroniza unidades de medida (ex: converter "1,85m" em float `1.85`) e trata valores ausentes para garantir uma base pronta para modelos de análise ou BI.

## 🛠️ Tecnologias Utilizadas

* **Python 3.x**
* **Pandas:** Manipulação e agregação de dados.
* **Cloudscraper & BeautifulSoup4:** Web scraping avançado.
* **SQLite3:** Armazenamento persistente dos dados coletados.
* **Regex:** Extração de padrões em URLs e strings de texto.

## 📊 Estrutura do Banco de Dados

Os dados são salvos em um arquivo SQLite (`scouting_sulamerica.db`). A tabela final consolidada inclui:
* **Identificação:** Nome, Idade, Nação, Posição, Clube.
* **Físico:** Altura e Pé Preferencial.
* **Mercado:** Valor de mercado convertido para numérico.
* **Performance:** Mais de 100 métricas (Gols, Assistências, xG, Passes Progressivos, Interceptações, etc.).

## 📖 Como Usar

1.  **Configuração da Liga:** No código de scraping do FBRef, altere a variável `link_da_vez` para a URL da liga desejada.
2.  **Configuração do Perfil:** No código do Transfermarkt, altere a variável `link_liga` para a página principal da liga no site.
3.  **Execução:** Rode as células em ordem. O script respeita intervalos de tempo (`time.sleep`) para evitar banimentos por excesso de requisições.

## ⚠️ Aviso Legal
Este projeto tem fins puramente educacionais e de estudo de análise de dados. Certifique-se de revisar os termos de uso dos sites citados antes de realizar raspagens em larga escala.
