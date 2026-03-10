# Render API Keep Alive v1.0

Pequeno projeto para evitar **cold start** em APIs hospedadas no Render (plano gratuito).

O workflow do GitHub Actions executa um **cron job a cada 5 minutos** que envia requisições para o endpoint `/health` da API, mantendo o container ativo.

---

# Como funciona

O GitHub Actions roda automaticamente um job agendado:

- executa a cada **5 minutos**
- envia **3 requisições HTTP**
- mantém a API ativa no Render

Fluxo:

1. GitHub Actions inicia
2. envia request `/health`
3. aguarda alguns segundos
4. envia novamente
5. repete mais uma vez
6. job finaliza

Isso evita que o Render coloque a API em **sleep mode**.

---

# Estrutura do projeto
