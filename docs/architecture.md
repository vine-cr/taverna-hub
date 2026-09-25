# Software Design Document (Architecture)

## 1. Tecnologias Utilizadas
- **Linguagens:** HTML5, CSS3, JavaScript.
- **Framework CSS:** Bootstrap v5.3.3 (utilizando Flexbox/Grid nativos).
- **Pré-processador:** Sass (SCSS) para modularização.
- **Bibliotecas JS:** jQuery e jQuery Mask Plugin.
- **Armazenamento Local:** Web Storage (localStorage/sessionStorage).

## 2. Design Tokens (Identidade Visual)
- **Cores Principais:**
  - `primary-color`: #8B4513 (Marrom Madeira / Taverna)
  - `secondary-color`: #D4AF37 (Dourado Velho)
  - `background-color`: #F5F5DC (Bege Pergaminho)
  - `text-color`: #212529 (Cinza Escuro)
- **Tipografia:**
  - `font-heading`: 'Cinzel', serif (Para títulos com visual épico)
  - `font-body`: 'Roboto', sans-serif (Para leitura fácil nos dados)

## 3. Entidades (JSON Server)
A persistência de dados usará duas entidades principais:
1. `campanhas` (id, nome, mestre, sistema, descricao)
2. `personagens` (id, campanhaId, nome, raca, classe, nivel)

## 4. Integração de API Pública
- **API Escolhida:** OpenWeather API v2.5.
- **Uso:** Será consumida na tela inicial para exibir o clima atual real e sugerir aos mestres uma "condição climática" para o início da sessão de RPG.

## 5. Componentes do Framework CSS
No protótipo visual, os seguintes elementos serão substituídos por componentes oficiais do Bootstrap 5 durante o desenvolvimento:
1. **Navbar:** A barra de navegação superior.
2. **Cards:** Os blocos que exibirão o resumo de cada campanha e personagem.
3. **Modal:** A janela flutuante que abrirá para confirmar a exclusão de um personagem.

## 6. Modelo de Dados (Diagrama ER)
```mermaid
erDiagram
    CAMPANHA ||--o{ PERSONAGEM : possui
    CAMPANHA {
        string id PK
        string nome
        string sistema
        string descricao
    }
    PERSONAGEM {
        string id PK
        string nome
        string raca
        string classe
        int nivel
        string campanhaId FK
    }