# 🎯 Descrição do Projeto

Este repositório é o resultado de um projeto Challenge-Based Learning (CBL) focado em levar o controle de versão Git além do básico (commit e push). 

O objetivo principal é estabelecer uma governança de dados robusta e auditável em um pipeline ELT/ETL, 
utilizando técnicas avançadas de Git para garantir a imutabilidade do histórico
e otimizar a colaboração em grandes repositórios de dados (Data Lakehouse - HDL).

# 💡 O Desafio Central: Auditoria e Rollback

Como garantir a rastreabilidade e a reversão seletiva (Rollback) de transformações incorretas (bugs) 
em um pipeline de dados críticos (Bronze -> Silver -> Gold) sem comprometer a auditoria ou reescrever o histórico?

# 🛠️ Tecnologias e Conceitos Chave

### Arquitetura
Data Lakehouse (HDL), ELT/ETL	

Estratégia de Branching (Git Flow/Trunk-Based)


### Governança
Auditoria, Imutabilidade, Qualidade	

git revert, git blame, Git Hooks


### Otimização
Monorepos, Colaboração, Assets Grandes	

git sparse-checkout, git LFS, git submodule


### Bancos de Dados
SQL, PL/SQL, NoSQL	

git rebase -i, git tag


# 🚀 Estrutura do Projeto (Fases CBL)

O repositório está organizado em cinco fases que simulam o ciclo de vida de um projeto de dados, 
onde cada fase tem um requisito técnico e um desafio de Git Avançado a ser dominado:

## Fase 1: Ingestão (Bronze)
- Foco Técnico: Extração de dados brutos de fontes Relacionais (SQLite) e Não Relacionais (TinyDB).

- Git Tópico: Decisão e Implementação da Estratégia de Branching (Ex: Git Flow vs. Trunk-Based Development).


## Fase 2: Refinamento (Silver)
- Foco Técnico: Limpeza, transformação (Python/Pandas) e integração dos dados brutos (ELT).

- Git Tópico: git rebase -i (Rebase Interativo) e Squash de Commits. 

  - Utilizado para limpar e consolidar o histórico de desenvolvimento antes do merge, garantindo que o histórico seja linear e legível.


## Fase 3: Agregação (Gold)
- Foco Técnico: Feature Engineering para Machine Learning e criação de Views agregadas (SQL) para Business Intelligence.

- Git Tópico: Git Hooks (pre-commit). 

  - Usado para forçar a validação da sintaxe (Python/SQL/PLSQL) e verificar a inclusão de credenciais ou outputs de Notebooks antes do commit.


## Fase 4: Auditoria e Rollback (O Ponto Crítico)
- Foco Técnico: Rastreamento e correção de um bug introduzido na lógica da camada Silver.

- Git Tópico:

  - Rastreamento: git blame e git bisect para localizar o commit defeituoso.

  - Correção Auditável: git revert. Cria um novo commit que desfaz o erro, crucial para a auditoria em produção. Diferente do git reset, que reescreveria a história.


## Fase 5: Integração, Otimização e Release
- Foco Técnico: Preparação final para deploy e otimização de performance.

- Git Tópico:

  - git submodule: Integração do código PL/SQL (Stored Procedures) como uma dependência rastreada.

  - git LFS: Gerenciamento de ativos No Code grandes (Dashboards/Modelos) sem inchar o repositório principal.

  - git sparse-checkout: Otimização para grandes equipes, permitindo que usuários baixem apenas as pastas necessárias (Ex: só 03_aggregation_gold/).

  - git tag: Marcação da versão final do pipeline como um Release imutável (v1.0.0-GOLD-RELEASE).


