# 🎯 Descrição do Projeto

Este repositório é o resultado de um projeto Challenge-Based Learning (CBL) focado em levar o controle de versão Git além do básico (commit e push). 

O objetivo principal é estabelecer uma governança de dados robusta e auditável em um pipeline ELT/ETL, 
utilizando técnicas avançadas de Git para garantir a imutabilidade do histórico
e otimizar a colaboração em grandes repositórios de dados (Data Lakehouse - HDL).

# 💡 O Desafio Central: Auditoria e Rollback

Como garantir a rastreabilidade e a reversão seletiva (Rollback) de transformações incorretas (bugs) 
em um pipeline de dados críticos (Bronze -> Silver -> Gold) sem comprometer a auditoria ou reescrever o histórico?

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


# 🎯 Git-Driven Data Governance: Pipeline ELT no Lakehouse

![DataOps](https://img.shields.io/badge/DataOps-Expert-blue?style=for-the-badge)
![Git](https://img.shields.io/badge/Git-Advanced-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

Este repositório é o resultado de um projeto **Challenge-Based Learning (CBL)** focado em elevar o controle de versão Git além do básico. O objetivo é estabelecer uma governança de dados robusta, auditável e resiliente em um pipeline ELT (Bronze -> Silver -> Gold).

## 💡 O Desafio Central
Como garantir a rastreabilidade e a reversão seletiva (**Rollback**) de transformações incorretas em um pipeline de dados críticos sem comprometer a auditoria ou reescrever o histórico?

---

## 🏗️ Arquitetura do Projeto (Fases CBL)

O projeto simula o ciclo de vida de um Data Lakehouse moderno, onde cada fase resolve um desafio técnico e um gargalo de governança:

### 🥉 Fase 1: Ingestão (Bronze)
* **Foco:** Extração de fontes SQLite e TinyDB.
* **Estratégia:** Implementação de **Trunk-Based Development** para agilidade.

### 🥈 Fase 2: Refinamento (Silver)
* **Foco:** Limpeza e integração com Python/Pandas.
* **Git Topic:** Uso de `git rebase -i` (Interactive Rebase) para manter um histórico linear e legível antes do merge.

### 🥇 Fase 3: Agregação (Gold)
* **Foco:** Business Intelligence e Feature Engineering.
* **Governança:** Implementação de **Git Hooks (pre-commit)** para validação de sintaxe e proteção de segredos.

### 🔍 Fase 4: Auditoria e Rollback (O Ponto Crítico)
* **Cenário:** Identificação de um bug na regra de impostos.
* **Ferramentas:** * `git bisect`: Busca binária automática para localizar o commit defeituoso.
    * `git blame`: Identificação do contexto e autor da alteração.
    * `git revert`: Correção auditável que preserva a imutabilidade do histórico.

### 🚀 Fase 5: Otimização e Release
* **Eficiência:** `git sparse-checkout` para download parcial do repo (ex: apenas camada Gold).
* **Assets Grandes:** `git LFS` para dashboards e modelos ML.

---

## 🛠️ Tecnologias e Ferramentas

| Categoria | Tecnologia |
| :--- | :--- |
| **Linguagens** | Python, SQL, PL/SQL |
| **Data Stack** | Pandas, SQLite, TinyDB |
| **DevOps/Git** | Git Advanced, Git Hooks, LFS |
| **Ambiente** | Google Colab / Terminal Linux |

---

## 📊 Governança de Storage: Git vs. Database

Decidimos onde cada asset reside com base em custo e versionamento:

| Asset | Localização | Método de Versão |
| :--- | :--- | :--- |
| Scripts (.py, .sql) | Git Core | Granular (Line-by-line) |
| Modelos/Dashboards | Git LFS | Snapshots binários |
| Dados (Parquet/DB) | Cloud/DB | Particionamento/Time-travel |

---

## 🧪 Como Reproduzir a Auditoria (Hands-on)

Você pode testar a inteligência deste repositório usando o script de validação automatizada:

1. **Inicie o Bisect:**
   ```bash
   git bisect start HEAD v1.0.0
