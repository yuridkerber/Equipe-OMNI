# 🤖 Omni

[![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)](#-status)

> **Atendimento inteligente e triagem automatizada de chamados de TI.**

---

## 📌 Sobre

O **Omni** é uma solução de atendimento interno baseada em **Inteligência Artificial**, desenvolvida para auxiliar funcionários na resolução e direcionamento de solicitações de TI.

A solução automatiza o primeiro atendimento, orientando o usuário em problemas simples e, quando necessário, coletando informações, classificando a solicitação e encaminhando o chamado para a equipe responsável.

---

## 🎯 Objetivo

Reduzir chamados simples, repetitivos ou direcionados incorretamente, tornando o suporte interno mais **rápido, organizado e eficiente**.

---

## 🏗️ Arquitetura

A arquitetura do Omni é dividida em **Frontend, Backend, Inteligência Artificial e Banco de Dados**.

```mermaid
flowchart TB
    subgraph Chat["Frontend — Chat (TypeScript)"]
        ChatUI["Chat Widget UI"]
        ChatComponents["Componentes"]
        ChatClient["Cliente HTTP/WebSocket"]
        ChatUI --> ChatComponents --> ChatClient
    end

    subgraph Admin["Frontend — ADM (React)"]
        AdmUI["Painel Administrativo"]
        AdmDashboard["Dashboard de Métricas"]
        AdmChamados["Gestão de Chamados"]
        AdmUsuarios["Gestão de Usuários"]
        AdmUI --> AdmDashboard
        AdmUI --> AdmChamados
        AdmUI --> AdmUsuarios
    end

    subgraph Backend["Backend (Go)"]
        API["API Gateway / REST"]
        Auth["Autenticação"]
        Tickets["Serviço de Chamados"]
        Routing["Serviço de Encaminhamento"]
        Orchestrator["Orquestrador de IA"]
        Metrics["Métricas"]
    end

    subgraph IA["Camada de IA — LLMs Locais"]
        KEV["KEV — Classificador"]
        Qwen["Qwen — Geração de Respostas"]
        Ollama["Ollama"]
    end

    DB[("PostgreSQL")]

    ChatClient -->|HTTP/WebSocket| API
    AdmDashboard --> API
    AdmChamados --> API
    AdmUsuarios --> API

    API --> Auth
    API --> Tickets
    API --> Orchestrator
    API --> Metrics

    Tickets --> Routing
    Tickets --> DB
    Auth --> DB
    Metrics --> DB

    Orchestrator --> KEV
    Orchestrator --> Qwen
    KEV --> Ollama
    Qwen --> Ollama

    Routing --> Tickets
```

O arquivo-fonte da arquitetura está disponível em [`arquitetura.puml`](./arquitetura.puml).

---

## 🧠 Inteligência Artificial

A camada de IA utiliza modelos locais para interpretar e responder às solicitações:

* **KEV** — classificação de intenção;
* **Qwen** — geração de respostas;
* **Ollama** — execução local dos modelos;
* **Orquestrador de IA** — integração da IA com o sistema.

---

## 🖥️ Sistema

### Chat

Interface destinada aos funcionários para realizar solicitações, receber orientações e acompanhar chamados.

### Painel Administrativo

Interface destinada ao gerenciamento de **chamados, usuários, encaminhamentos e métricas**.

---

## 🛠️ Tecnologias

### Backend

[![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge\&logo=go\&logoColor=white)](https://go.dev/)

### Frontend

[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge\&logo=typescript\&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge\&logo=react\&logoColor=black)](https://react.dev/)

### Banco de Dados

[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge\&logo=postgresql\&logoColor=white)](https://www.postgresql.org/)

### Inteligência Artificial

[![Ollama](https://img.shields.io/badge/Ollama-000000?style=for-the-badge\&logo=ollama\&logoColor=white)](https://ollama.com/)
[![Qwen](https://img.shields.io/badge/Qwen-LLM-6E56CF?style=for-the-badge)](https://qwenlm.github.io/)

### Arquitetura e Versionamento

[![PlantUML](https://img.shields.io/badge/PlantUML-4B4B4B?style=for-the-badge)](https://plantuml.com/)
[![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge\&logo=git\&logoColor=white)](https://git-scm.com/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge\&logo=github\&logoColor=white)](https://github.com/)

> **Comunicação:** REST API e WebSocket.

---

## 🎨 Protótipo

O protótipo das interfaces está sendo desenvolvido no **Figma**.

[![Figma](https://img.shields.io/badge/Prot%C3%B3tipo-Figma-F24E1E?style=for-the-badge\&logo=figma\&logoColor=white)](https://www.figma.com/proto/BQI0OtXmf1BAuWfHsxSYw0/modelo-PI-celular?node-id=11-16&p=f&t=uYYT4EW0nWHuNZm5-1&scaling=scale-down&content-scaling=fixed&page-id=0%3A1)

---

## 👥 Equipe

| Integrante | GitHub | LinkedIn |
| :--- | :---: | :---: |
| **Yuri Duarte** | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/yuridkerber) | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yuri-kerber-a1825b3b0/) |
| **Karen Marroco** | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/KarenMarroco) | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://br.linkedin.com/in/karen-marroco-4b6016180) |
| **Miguel Giovannini** | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/Giovannini150) | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/miguel-ricardo-giovannini-40a6a3361/) |
| **Matheus Basso** | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/MTBasso) | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](#) |
---

## 📌 Status

🟡 **Em desenvolvimento**

* [x] Planejamento inicial
* [x] Definição da arquitetura
* [x] Prototipação inicial
* [ ] Validação dos requisitos
* [ ] Implementação do backend
* [ ] Implementação das interfaces
* [ ] Integração com IA
* [ ] Sistema de chamados
* [ ] Testes e validação
* [ ] Documentação final

---

## 🎓 Projeto Integrador

Projeto acadêmico desenvolvido para a disciplina de **Projeto Integrador**, aplicando conceitos de **Engenharia de Software, desenvolvimento de sistemas e Inteligência Artificial**.
