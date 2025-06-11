# GitFlow - Fluxo de Trabalho com Git

O **GitFlow** é uma estratégia de branching (ramificação) criada para organizar o desenvolvimento de software de forma clara, previsível e colaborativa. Ele define papéis bem estabelecidos para diferentes branches e momentos do ciclo de vida de um projeto.

![[gitflow_sample.png]]

---

## 🌳 Estrutura de Branches

### 1. `main`

- Contém o código **em produção**.
    
- Cada commit nesta branch corresponde a uma versão estável.
    

### 2. `develop`

- Contém o código com os recursos **em desenvolvimento**.
    
- Base para novas features, integrações e testes.
    

### 3. `feature/*`

- Usada para desenvolver **novas funcionalidades**.
    
- Nome sugestivo: `feature/login-api`, `feature/novo-pipeline`
    
- Criação:
    
    ```bash
    git checkout develop
    git checkout -b feature/nome-da-feature
    ```
    
- Após terminar:
    
    ```bash
    git checkout develop
    git merge feature/nome-da-feature
    git branch -d feature/nome-da-feature
    ```
    

### 4. `release/*`

- Usada para preparar uma **nova versão de produção**.
    
- Permite últimos ajustes e testes.
    
- Criação:
    
    ```bash
    git checkout develop
    git checkout -b release/1.2.0
    ```
    
- Ao finalizar:
    
    ```bash
    git checkout main
    git merge release/1.2.0
    git tag -a v1.2.0 -m "Release 1.2.0"
    
    git checkout develop
    git merge release/1.2.0
    git branch -d release/1.2.0
    ```
    

### 5. `hotfix/*`

- Corrige **problemas críticos em produção**.
    
- Criação:
    
    ```bash
    git checkout main
    git checkout -b hotfix/bug-urgente
    ```
    
- Após correção:
    
    ```bash
    git commit -m "Corrige bug urgente"
    git checkout main
    git merge hotfix/bug-urgente
    git tag -a v1.2.1 -m "Hotfix 1.2.1"
    
    git checkout develop
    git merge hotfix/bug-urgente
    git branch -d hotfix/bug-urgente
    ```
    

---

## 📌 Regras Gerais

- Sempre criar branches a partir da base correta (`develop` para features, `main` para hotfixes).
    
- Nomear as branches de forma clara e descritiva.
    
- Fazer pull requests (PRs) com revisão de código.
    
- Usar tags para marcar releases no `main`.
    

---

## ✅ Quando usar GitFlow?

Ideal para times com:

- Ciclos de release bem definidos
    
- Ambientes separados de homologação e produção
    
- Vários desenvolvedores trabalhando em paralelo
    

Para projetos menores ou mais ágeis, alternativas como trunk-based ou GitHub Flow podem ser mais simples.

---

**Referência**: [GitFlow original por Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/)