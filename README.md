# 🧾 **DOCUMENTAÇÃO DO PROJETO ELEKTRON SEGURITY**

## 📘 1. Visão Geral do Projeto

O sistema **Elektron Segurity** é um **protótipo web** desenvolvido utilizando **Spring Boot (Java 17)** no back-end e **Vue.js via CDN** no front-end, com o objetivo de **gerenciar categorias, produtos, clientes e orçamentos de uma empresa de segurança eletrônica**.

A aplicação segue uma **arquitetura cliente-servidor**, onde:

* O **cliente (front-end)** consome a API via **Axios (HTTP)**;
* O **servidor (back-end)**, em Spring Boot, processa as requisições e realizará persistência de dados em banco;
* O **banco de dados** (futuro) será configurado para armazenar categorias, produtos, clientes e orçamentos;
* O projeto também prevê integração futura com **Firebase**, para autenticação e hospedagem de dados.

---

## 🧩 2. Tecnologias Utilizadas

| Camada                      | Tecnologia            | Descrição                                                             |
| --------------------------- | --------------------- | --------------------------------------------------------------------- |
| **Front-end**               | Vue.js (CDN)          | Framework JavaScript reativo para construção da interface de usuário. |
|                             | Bootstrap 5           | Biblioteca CSS para design responsivo e moderno.                      |
|                             | Axios                 | Cliente HTTP usado para se comunicar com a API do back-end.           |
| **Back-end**                | Spring Boot (Java 17) | Framework para construção do servidor e APIs REST.                    |
| **Banco de Dados (futuro)** | H2 / MySQL / Firebase | O projeto iniciará com H2 e depois poderá integrar Firebase.          |
| **Controle de versão**      | Git/GitHub            | Armazenamento e versionamento do código.                              |

---

## 🧭 3. Estrutura de Telas do Front-End

O front-end é composto por **cinco seções principais**, acessadas pelo menu de navegação superior:

| Seção                   | Função                                                    |
| ----------------------- | --------------------------------------------------------- |
| **Início (Home)**       | Apresenta a introdução do sistema.                        |
| **Categorias**          | Permite criar e excluir categorias de produtos.           |
| **Produtos**            | Permite cadastrar produtos vinculados a categorias.       |
| **Clientes**            | Cadastra informações básicas dos clientes.                |
| **Orçamentos (Quotes)** | Cria orçamentos com múltiplos produtos e calcula o total. |

Cada seção é controlada dinamicamente por uma variável Vue chamada `view`, que alterna as telas sem recarregar a página.

---

## ⚙️ 4. Funcionalidades Atuais

### ✅ Implementadas até o momento:

* Interface reativa feita em Vue.js, totalmente funcional no navegador;
* Navegação entre telas sem recarregar a página;
* Cadastro local (via API simulada) de:

  * Categorias
  * Produtos
  * Clientes
  * Orçamentos
* Cálculo automático de subtotal e total em orçamentos;
* Layout responsivo utilizando Bootstrap;
* Estrutura pronta para integração com o back-end Spring Boot (`http://localhost:8080/api/...`).

### ⚠️ Pendências (próximas etapas):

* Implementação das rotas REST no back-end;
* Persistência em banco de dados;
* Autenticação e login via Firebase;
* Deploy em ambiente local ou nuvem.

---

## 🚀 5. Desenvolvimento Dividido em 5 Sprints

---

### 🟩 **SPRINT 1 — Planejamento e Estrutura Inicial**

**Objetivo:**
Definir o escopo do sistema, tecnologias e criar o esqueleto do projeto.

**Atividades realizadas:**

* Criação do projeto Spring Boot com Java 17.
* Configuração inicial do Vue.js via CDN no arquivo `index.html`.
* Criação da navbar e navegação entre telas (`view` controlado por Vue).
* Estruturação visual com Bootstrap 5.

**Entregáveis:**

* Protótipo navegável com interface básica.
* Documento de requisitos iniciais.
* Repositório inicial no GitHub.

**Próximos passos:**

* Criar estrutura de entidades no back-end (Category, Product, Client, Quote).
* Definir endpoints REST.

---

### 🟦 **SPRINT 2 — Desenvolvimento do Front-End Dinâmico**

**Objetivo:**
Implementar o comportamento interativo das telas usando Vue.js.

**Atividades realizadas:**

* Criação de formulários para:

  * Categorias (cadastro e exclusão);
  * Produtos (com vínculo de categoria);
  * Clientes (nome, e-mail e telefone);
  * Orçamentos (seleção de cliente, produtos, quantidades e cálculo automático).
* Implementação de armazenamento temporário e comunicação com `axios`.

**Entregáveis:**

* Interface 100% funcional (sem back-end real).
* Teste de usabilidade no navegador.
* Função de cálculo de total automático no orçamento.

**Próximos passos:**

* Conectar as rotas `/api/categories`, `/api/products`, `/api/clients`, `/api/quotes` com o back-end Spring Boot.

---

### 🟨 **SPRINT 3 — Integração com o Back-End (Spring Boot)**

**Objetivo:**
Desenvolver a API RESTful que o front-end já consome.

**Atividades planejadas:**

* Criação das classes modelo:

  * `Category`, `Product`, `Client`, `Quote`, `QuoteItem`.
* Implementação dos controladores (`@RestController`):

  * `/api/categories`
  * `/api/products`
  * `/api/clients`
  * `/api/quotes`
* Implementação dos repositórios JPA.
* Configuração inicial do banco H2 (em memória).

**Entregáveis esperados:**

* API funcional acessível via `localhost:8080/api/...`.
* Front-end recebendo e enviando dados reais.
* Dados persistidos no H2.

---

### 🟧 **SPRINT 4 — Persistência e Firebase**

**Objetivo:**
Configurar persistência definitiva e autenticação.

**Atividades planejadas:**

* Substituição do H2 por MySQL ou PostgreSQL.
* Configuração da integração com **Firebase**:

  * Autenticação de usuários (login/logout).
  * Possível sincronização de dados (Firestore).
* Implementação de segurança com `Spring Security` + JWT.
* Integração do login Firebase no front-end.

**Entregáveis esperados:**

* Sistema com login seguro.
* Controle de acesso a rotas do front-end.
* Dados persistidos e autenticados.

---

### 🟥 **SPRINT 5 — Testes, Documentação e Deploy**

**Objetivo:**
Finalizar o protótipo, documentar e preparar para apresentação/deploy.

**Atividades planejadas:**

* Testes de integração entre Vue.js e Spring Boot.
* Documentação do código e endpoints.
* Geração de relatório de sprints (este documento).
* Deploy local (ou em Firebase Hosting / Render / Railway).
* Validação de todas as telas e persistência.

**Entregáveis esperados:**

* Protótipo funcional completo.
* Documentação técnica e de usuário.
* Vídeo de demonstração ou manual ilustrado.

---

## 🧱 6. Arquitetura do Sistema

```text
Front-end (Vue.js CDN)
    |
    |  Axios HTTP (JSON)
    v
Back-end (Spring Boot)
    |
    |  JPA / JDBC
    v
Banco de Dados (H2 -> MySQL / Firebase)
```

---

## 📡 7. API Planejada (Endpoints)

| Entidade      | Método | Endpoint               | Descrição         |
| ------------- | ------ | ---------------------- | ----------------- |
| **Categoria** | GET    | `/api/categories`      | Listar categorias |
|               | POST   | `/api/categories`      | Criar categoria   |
|               | DELETE | `/api/categories/{id}` | Excluir categoria |
| **Produto**   | GET    | `/api/products`        | Listar produtos   |
|               | POST   | `/api/products`        | Criar produto     |
|               | DELETE | `/api/products/{id}`   | Excluir produto   |
| **Cliente**   | GET    | `/api/clients`         | Listar clientes   |
|               | POST   | `/api/clients`         | Criar cliente     |
| **Orçamento** | GET    | `/api/quotes`          | Listar orçamentos |
|               | POST   | `/api/quotes`          | Criar orçamento   |

---

## 📖 8. Próximas Etapas Técnicas

1. Criar o back-end Spring Boot com as rotas descritas.
2. Configurar o banco de dados H2 (ou MySQL) no `application.properties`.
3. Testar integração front + back.
4. Configurar Firebase para login (via SDK JavaScript e autenticação de email/senha).
5. Hospedar projeto (Firebase Hosting, Render, ou GitHub Pages).

---

## 📚 9. Conclusão Parcial

Até o momento, o projeto **Elektron Segurity** encontra-se com **o front-end completo, responsivo e funcional**, preparado para integração com o back-end em Spring Boot.
O código segue boas práticas de componentização via Vue.js e consumo de API REST via Axios.

Os próximos passos envolvem a **implementação da API, persistência em banco e autenticação via Firebase**, o que consolidará o sistema como uma aplicação web completa, integrando todas as camadas de um ambiente real de desenvolvimento full stack.

Deseja que eu gere algum desses arquivos também (por exemplo, o README técnico do projeto)?
