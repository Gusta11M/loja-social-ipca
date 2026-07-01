# Loja Social IPCA – Sistema Integrado de Apoio Social

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Kotlin](https://img.shields.io/badge/Kotlin-Jetpack%20Compose-7F52FF?logo=kotlin)](app)
[![React](https://img.shields.io/badge/React-Vite%20%2B%20TS-61DAFB?logo=react)](web)
[![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%7C%20Auth%20%7C%20Functions-FFCA28?logo=firebase)](functions)

Sistema digital completo para modernizar e otimizar a gestão da Loja Social do IPCA, substituindo processos manuais por uma solução centralizada que promove transparência e entreajuda na comunidade académica.

O projeto é um **monorepo** com três componentes:

| Pasta | Descrição | Stack |
|---|---|---|
| [`app/`](app) | Aplicação móvel Android — usada por beneficiários e colaboradores do SAS | Kotlin, Jetpack Compose, MVVM + Clean Architecture, Hilt |
| [`web/`](web) | Site público de apresentação e transparência (campanhas, doações, estado de stock) | React, Vite, TypeScript, Tailwind, shadcn/ui |
| [`functions/`](functions) | Cloud Functions — envio de emails e notificações push | Node.js, Firebase Functions v2, Nodemailer |

---

## Funcionalidades Principais

### Gestão de Beneficiários
* **Registo Digital:** Fluxo sequencial para recolha de dados pessoais, académicos e submissão de documentos obrigatórios (RGPD).
* **Candidaturas (Requerimentos):** Submissão e monitorização do estado do pedido de apoio (Submetido, Em Análise, Em Falta, Aprovado ou Rejeitado).
* **Perfil Autónomo:** Autonomia para o beneficiário consultar o histórico de apoios e editar dados pessoais.

### Gestão de Inventário (Bens)
* **Controlo de Stock:** Diferenciação entre catálogo de produtos (tipologia) e stock físico (quantidades e lotes).
* **Categorização:** Organização por tipos de bens: Alimentares, Higiene Pessoal e Limpeza.
* **Gestão de Validades:** Monitorização de datas de validade com sistema de notificações automáticas para evitar desperdícios.

### Gestão de Entregas
* **Agendamento Flexível:** Calendarização de levantamentos mensais com opção de repetição automática.
* **Notificações:** Alertas *push* e e-mails para relembrar os beneficiários das datas de entrega.
* **Validação Operacional:** Registo imediato do estado da entrega (Entregue/Não Entregue) por parte dos colaboradores do SAS.

### Campanhas e Comunidade
* **Monitorização de Campanhas:** Gestão do ciclo de vida de iniciativas de recolha internas e externas.
* **Site Público:** Página web com informação sobre campanhas, doações e transparência de stock.

---

## Stack Tecnológica

**App Android**
* **Linguagem:** Kotlin
* **UI:** Jetpack Compose + Compose Navigation
* **Arquitetura:** MVVM (Model-View-ViewModel) + Clean Architecture
* **Injeção de Dependências:** Hilt

**Web**
* **Framework:** React + Vite + TypeScript
* **UI:** Tailwind CSS + shadcn/ui (Radix primitives)

**Backend (Firebase, partilhado por App e Web)**
* **Firestore:** Armazenamento de dados NoSQL
* **Authentication:** Autenticação de utilizadores
* **Storage:** Armazenamento de imagens (produtos/campanhas)
* **Cloud Functions:** Envio de e-mails (Nodemailer) e notificações push (FCM)

---

## Organização do Código

O projeto (app Android) segue os princípios de **Clean Architecture**, dividindo-se em:

1. **Domain:** Lógica de negócio pura (Use Cases e Modelos de Domínio).
2. **Data:** Repositórios e Data Sources (integração com Firebase).
3. **Presentation:** Camada de UI organizada por ecrãs (`Screens`), componentes reutilizáveis (`Components`) e gestão de estado (`ViewModels`).

---

## Como Configurar e Executar

### 1. Clonar o Repositório

```bash
git clone https://github.com/Gusta11M/loja-social-ipca.git
cd loja-social-ipca
```

### 2. App Android (`app/`)

1. Cria um projeto na [Consola do Firebase](https://console.firebase.google.com/).
2. Adiciona uma app Android com o package `pt.ipca.lojasocial`.
3. Faz o download do `google-services.json` e coloca-o em `app/`.
4. Abre o projeto no **Android Studio**, sincroniza o Gradle e corre num emulador/dispositivo com API 24+.

### 3. Web (`web/`)

```bash
cd web
cp .env.example .env   # preenche com as credenciais do teu projeto Firebase
npm install
npm run dev
```

### 4. Cloud Functions (`functions/`)

```bash
cd functions
cp .env.example .env   # credenciais SMTP (Gmail App Password), nunca comitar
npm install
firebase deploy --only functions
```

> **Nota de segurança:** todas as credenciais (`google-services.json`, `.env`, chaves de assinatura) estão excluídas via `.gitignore` e nunca devem ser comitadas. Usa sempre os ficheiros `.env.example` como referência.

---

## Licença

Distribuído sob licença MIT. Consulta [LICENSE](LICENSE) para mais detalhes.

---

## Equipa (Projeto Aplicado & Programação Dispositivos Móveis)
* 27962 Gustavo Daniel Loureiro Marques
* 29852 Gustavo da Costa Pereira
* 23010 Hugo Tiago Mendes Cruz
* 27977 Igor Miguel Torres da Costa
* 23016 Dani Carvalho da Cruz
* **Orientação:** Prof.ª Patrícia Isabel Sousa Trindade Silva Leite & Prof.º Lourenço Miguel Araújo Gomes

---
**Escola Superior de Tecnologia – IPCA**
Licenciatura em Engenharia de Sistemas Informáticos
