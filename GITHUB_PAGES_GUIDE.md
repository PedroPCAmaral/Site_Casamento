# 🚀 Guia Completo: Publicar no GitHub Pages

Este guia mostra como publicar o site de casamento no GitHub Pages de forma automática e funcional.

## 📋 Pré-requisitos

- Conta no GitHub
- Git instalado no seu computador
- Node.js 18+ instalado

## 🎯 Opção 1: Deploy Automático com GitHub Actions (RECOMENDADO)

Esta é a forma mais fácil! O site será publicado automaticamente sempre que você fizer push para a branch `main`.

### Passo 1: Criar o Repositório no GitHub

1. Acesse [GitHub.com](https://github.com)
2. Clique no ícone **+** no canto superior direito
3. Selecione **New repository**
4. Preencha os dados:
   - **Repository name**: `wedding-dream-site`
   - **Description**: "Site elegante de planejamento e celebração de casamento"
   - **Visibility**: **Public** (necessário para GitHub Pages)
   - **Initialize this repository with**: Deixe desmarcado

5. Clique em **Create repository**

### Passo 2: Fazer Push do Código

No terminal, execute:

```bash
# Navegue até a pasta do projeto
cd wedding-dream-site

# Inicialize o git (se ainda não estiver)
git init

# Adicione o remote (substitua SEU_USUARIO pelo seu usuário do GitHub)
git remote add origin https://github.com/SEU_USUARIO/wedding-dream-site.git

# Adicione todos os arquivos
git add .

# Faça o commit
git commit -m "Initial commit: Wedding planning website"

# Renomeie a branch para main
git branch -M main

# Faça push para o GitHub
git push -u origin main
```

### Passo 3: Ativar GitHub Pages

1. Vá para o repositório no GitHub
2. Clique em **Settings** (Configurações)
3. No menu lateral esquerdo, clique em **Pages**
4. Em "Build and deployment":
   - **Source**: Selecione **GitHub Actions**
   - O workflow já está configurado automaticamente!

5. Aguarde alguns minutos e o site será publicado em:
   ```
   https://SEU_USUARIO.github.io/wedding-dream-site/
   ```

### Passo 4: Verificar o Deploy

1. Volte para a página principal do repositório
2. Clique em **Actions** (Ações)
3. Veja o workflow `Deploy to GitHub Pages` em execução
4. Quando ficar verde ✅, o site está publicado!

---

## 🎯 Opção 2: Deploy Manual (Alternativa)

Se preferir fazer o deploy manualmente:

### Passo 1: Build Local

```bash
cd wedding-dream-site
npm install
GITHUB_PAGES=true npm run build
```

### Passo 2: Deploy com gh-pages

```bash
# Instale o gh-pages (uma única vez)
npm install --save-dev gh-pages

# Adicione ao package.json (já incluído no projeto)
# "deploy": "gh-pages -d dist/public"

# Faça o deploy
npm run deploy
```

---

## 🌐 Usar Domínio Personalizado (Opcional)

Se você tiver um domínio personalizado:

### Passo 1: Adicionar CNAME

1. Crie um arquivo `CNAME` na raiz do projeto com seu domínio:
   ```
   seu-dominio.com
   ```

2. Faça commit e push:
   ```bash
   git add CNAME
   git commit -m "Add custom domain"
   git push
   ```

### Passo 2: Configurar DNS

Consulte a documentação do seu provedor de domínio para apontar para:
```
SEU_USUARIO.github.io
```

### Passo 3: Ativar HTTPS

1. Vá para **Settings > Pages**
2. Marque **Enforce HTTPS**

---

## 🔄 Atualizar o Site

Depois que o site estiver publicado, qualquer mudança é simples:

```bash
# Faça suas alterações no código

# Adicione os arquivos
git add .

# Faça commit
git commit -m "Descrição das mudanças"

# Faça push
git push
```

O GitHub Actions fará o deploy automaticamente em poucos minutos!

---

## ✅ Checklist de Publicação

- [ ] Repositório criado no GitHub
- [ ] Código feito push para a branch `main`
- [ ] GitHub Pages ativado
- [ ] Workflow `Deploy to GitHub Pages` executado com sucesso
- [ ] Site acessível em `https://SEU_USUARIO.github.io/wedding-dream-site/`
- [ ] Todas as seções carregando corretamente
- [ ] Links de navegação funcionando

---

## 🐛 Solução de Problemas

### O site não aparece após fazer push

**Solução:**
1. Vá para **Settings > Pages**
2. Verifique se **Source** está configurado como **GitHub Actions**
3. Vá para **Actions** e veja se o workflow está em execução
4. Se houver erro, clique no workflow para ver os logs

### Links não funcionam (erro 404)

**Causa:** O base path não está correto

**Solução:** O arquivo `vite.config.ts` já está configurado com:
```typescript
base: process.env.GITHUB_PAGES ? '/wedding-dream-site/' : '/',
```

Isso garante que os links funcionem corretamente no GitHub Pages.

### Estilos não carregam

**Causa:** Caminho de CSS incorreto

**Solução:** Já está corrigido no projeto! Os estilos Tailwind CSS carregam corretamente.

### Imagens não aparecem

**Causa:** Caminho de imagens incorreto

**Solução:** Se adicionar imagens, use caminhos relativos:
```jsx
<img src="/wedding-dream-site/imagem.jpg" alt="descrição" />
```

---

## 📊 Monitorar Deployments

1. Vá para o repositório
2. Clique em **Deployments** (Implantações)
3. Veja o histórico de todos os deployments
4. Clique em um deployment para ver detalhes

---

## 🎓 Próximas Melhorias

Depois de publicar, você pode:

1. **Adicionar formulário de RSVP** — Integrar com um serviço como Formspree
2. **Adicionar galeria de fotos** — Usar um serviço como Cloudinary
3. **Adicionar contador regressivo** — Já implementado, apenas customize a data
4. **Usar domínio personalizado** — Siga as instruções acima

---

## 📞 Suporte

Se tiver dúvidas:

1. Consulte a [documentação oficial do GitHub Pages](https://docs.github.com/en/pages)
2. Veja os [logs do GitHub Actions](https://github.com/SEU_USUARIO/wedding-dream-site/actions)
3. Verifique se há erros de build em **Actions > Workflow runs**

---

## 🎉 Pronto!

Seu site de casamento está publicado e acessível para toda a internet! 🌍

**URL do site**: `https://SEU_USUARIO.github.io/wedding-dream-site/`

Compartilhe com amigos e família! 💍

---

**Desenvolvido com ❤️ para o casamento dos sonhos de João e Maria**
