# TRABALHO-FINAL-BANCO-DE-DADOS-VETORIAL

# 📝 README – Sistema de Chatbot com Banco de Dados Vetorial

## 👤 Integrantes

* **Ítalo Gabriel**
* **Nicolas Alexandrino**

## 🎓 Instituição

**Faculdade Santo Agostinho (FSA)**
Curso: **Engenharia de Software**
Disciplina: **Projeto de Banco de Dados**
Professor: **Anderson Soares**

---

# 📌 Nome do Projeto

**Chatbot Inteligente com Busca Semântica usando Banco de Dados Vetorial**

---

# 🧩 Descrição do Problema

O projeto tem como objetivo desenvolver um **chatbot inteligente** capaz de responder perguntas com base no conteúdo de **documentos enviados pelo usuário**.

O fluxo funciona assim:

1. O usuário envia um arquivo para o **Google Drive**.
2. O **n8n** detecta o upload, extrai o texto e converte em **embeddings**.
3. Esses embeddings são armazenados no **Supabase (pgvector)**.
4. Quando uma pergunta é enviada, ela também é convertida em embedding.
5. O sistema retorna os trechos mais semelhantes usando **busca semântica**.
6. A IA gera uma resposta contextualizada utilizando **RAG (Retrieval-Augmented Generation)**.

💡 O objetivo é criar um sistema escalável que permita consultas inteligentes sem depender de palavras exatas, mas sim do significado do texto.

---

# 🛠 Tecnologias Usadas

* **n8n** — Automação e orquestração do fluxo
* **Google Drive** — Upload e armazenamento de arquivos de entrada
* **Supabase + pgvector** — Banco de dados vetorial
* **OpenAI** — Geração de embeddings e respostas do chatbot
* **OpenAI Chat Model** – Composição final da resposta
* **Workflows n8n** — Responsáveis pela lógica completa

---

# 🎥 Link do Vídeo

👉 *(https://drive.google.com/file/d/1fTvLQNT7H6ZWvrAMj0PmvIGjXMIQT1d4/view?usp=sharing)*


---

# ▶️ Como Executar o Projeto

### **1. Configurar o Supabase**

* Criar um banco de dados no Supabase.
* Ativar a extensão `pgvector`:

  ```sql
  create extension vector;
  ```
* Criar a tabela para armazenar embeddings:

  ```sql
  create table documentos (
      id bigserial primary key,
      conteudo text,
      metadata jsonb,
      embedding vector(1536)
  );
  ```

### **2. Configurar credenciais no n8n**

No n8n, configurar:

* Credencial do **Google Drive**
* Credencial do **Supabase**
* Credencial da **OpenAI**

### **3. Importar o workflow**

* Importar o arquivo `.json` da pasta `/workflow/`.
* Configurar caminhos, IDs e chaves conforme sua conta.

### **4. Executar o fluxo**

* Enviar um arquivo para o Google Drive
* Rodar o workflow de **indexação (embeddings)**
* Testar o workflow de **chat** enviando perguntas

---

# 🖼 Prints do Funcionamento

### ✔️ Fluxo completo no n8n

<img width="1906" height="952" alt="Captura de tela 2025-12-03 155933" src="https://github.com/user-attachments/assets/502dba98-0972-4d15-b21d-81802f432c98" />


### ✔️ Execução do chat usando busca semântica


<img width="1901" height="946" alt="Captura de tela 2025-12-03 160249" src="https://github.com/user-attachments/assets/3bebbe8c-bf1e-4fe4-8505-adba3aa0de9f" />

### ✔️ Log da resposta gerada pela IA

<img width="1841" height="711" alt="Captura de tela 2025-12-03 160305" src="https://github.com/user-attachments/assets/6f75bc73-7f88-4066-abbd-5a09da41928f" />


