# 🚀 Deploy na Streamlit Cloud

## Pré-requisitos

1. ✅ Conta no GitHub com repositório público ou privado
2. ✅ Conta na Streamlit Cloud (https://share.streamlit.io)
3. ✅ Chave API da Anthropic (https://console.anthropic.com)

---

## Passo a Passo

### 1. Commit das alterações no GitHub

```bash
git add .
git commit -m "Preparação para deploy na Streamlit Cloud"
git push origin main
```

### 2. Acessar Streamlit Cloud

1. Acesse: https://share.streamlit.io
2. Clique em **"Sign in"** e faça login com sua conta GitHub
3. Autorize o Streamlit a acessar seus repositórios

### 3. Criar novo App

1. Clique em **"New app"**
2. Preencha:
   - **Repository**: `LeonardoRFragoso/Agente-Multi-Agentes-de-Negocio-com-Streamlit`
   - **Branch**: `main`
   - **Main file path**: `app.py`

### 4. Configurar Secrets (IMPORTANTE!)

Antes de fazer deploy, configure a chave da API:

1. Clique em **"Advanced settings"** (antes de Deploy)
2. Na seção **"Secrets"**, adicione:

```toml
ANTHROPIC_API_KEY = "sua-chave-anthropic-aqui"
```

3. Clique em **"Save"**

### 5. Deploy

1. Clique em **"Deploy!"**
2. Aguarde o build (pode levar 2-5 minutos)
3. Seu app estará disponível em: `https://seu-app.streamlit.app`

---

## Estrutura de Arquivos para Deploy

```
projeto/
├── .streamlit/
│   ├── config.toml          # Tema e configurações
│   └── secrets.toml.example # Exemplo de secrets (NÃO commitar o real!)
├── app.py                    # Arquivo principal
├── requirements.txt          # Dependências Python
├── .gitignore               # Ignora .env e secrets.toml
└── ... outros arquivos
```

---

## Troubleshooting

### ❌ Erro: "No module named 'xxx'"
- Verifique se o pacote está no `requirements.txt`
- Use versões flexíveis: `package>=1.0.0` ao invés de `package==1.0.0`

### ❌ Erro: "ANTHROPIC_API_KEY not found"
- Configure a chave em **Settings > Secrets** no Streamlit Cloud
- Formato: `ANTHROPIC_API_KEY = "sk-ant-..."`

### ❌ Erro com WeasyPrint
- WeasyPrint foi removido pois requer dependências do sistema
- Use apenas PDF via ReportLab (já configurado)

### ❌ App muito lento
- Primeira execução é mais lenta (cold start)
- Execuções subsequentes são mais rápidas

---

## Atualizar o App

Qualquer `git push` para o branch `main` atualiza automaticamente o app!

```bash
git add .
git commit -m "Atualização"
git push origin main
```

O Streamlit Cloud detecta mudanças e faz redeploy automático.

---

## URLs Úteis

- **Streamlit Cloud**: https://share.streamlit.io
- **Anthropic Console**: https://console.anthropic.com
- **Documentação Streamlit**: https://docs.streamlit.io/streamlit-community-cloud
