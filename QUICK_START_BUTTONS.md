# ⚡ Quick Start - Verificar Botões Tab 4

**Tempo Estimado**: 2 minutos  
**Objetivo**: Verificar que os botões estão funcionando após a correção

---

## 🚀 3 Passos Rápidos

### Passo 1: Cadastre UM Fornecedor (30 seg)
```
1. Clique "🏢 Cadastro Fornecedor"
2. Preencha:
   - Nome: SIEMENS
   - Email: siemens@test.com
   - CNPJ: 12.345.678/0001-90
   - Telefone: 1133334444
   - UF: SP (dropdown)
   - Cidade: São Paulo
3. Clique "✓ Cadastrar Fornecedor"
4. Verifique notificação ✅
```

### Passo 2: Crie UM Processo (30 seg)
```
1. Clique "➕ Novo Processo"
2. Preencha:
   - Número DATAGED: DG-2025-001
   - Descrição: Teste
   - Centro de Custo: CC-001
   - Responsável: Seu Nome
   - Tipo: Cabos
3. Clique "Criar Processo"
4. Verifique redirecionamento ✅
```

### Passo 3: Teste os Botões (1 min)
```
1. Clique "⚖️ Equalização" (Tab 4)
2. No dropdown, selecione "DG-2025-001"
3. ✅ BOTÕES DEVEM APARECER ATIVOS:
   - "+ Adicionar Proposta" → ATIVO
   - "+ Adicionar Item" → ATIVO
   - "💾 Salvar" → ATIVO
4. Clique "+ Adicionar Proposta"
5. ✅ Verifique notificação "✓ Proposta adicionada"
6. Clique "+ Adicionar Item"
7. Preencha:
   - Tipo: Cabo
   - Código: 100101
   - Descrição: Teste
   - Qtd: 100
8. ✅ Verifique notificação de sucesso
9. Clique "💾 Salvar"
10. ✅ Verifique localStorage foi atualizado (DevTools F12 → Application)
```

---

## ✅ Checklist de Validação

- [ ] Botão "+ Adicionar Proposta" responde a clique
- [ ] Botão "+ Adicionar Item" responde a clique
- [ ] Botão "💾 Salvar" responde a clique
- [ ] Notificações aparecem
- [ ] Container de equalização fica visível
- [ ] Dados persistem em localStorage

---

## 🎯 Se algo não funcionar

### Tab 4 não abre
```
Abra DevTools (F12) → Console
Procure por erros vermelhos
Recarregue a página (Ctrl+R)
```

### Botões não respondem
```
DevTools (F12) → Application → localStorage
Procure por "processos_amazon"
Verifique se o processo foi salvo
Se não, crie novamente em Tab 1
```

### Recarregue a página inteira
```
Ctrl+Shift+Delete para limpar cache
Abra teste_app.html novamente
Tente os passos acima de novo
```

---

## 📊 O que Mudou

**Antes**: Clicava em Tab 4 → Nada acontecia (container oculto, botões inacessíveis)

**Depois**: Clicava em Tab 4 → Container aparece → Botões ficam ativos → Tudo funciona ✅

---

**Se os botões não funcionarem após seguir este guia, abra uma issue com:**
- Screenshot do problema
- Console log (F12 → Console)
- Passos exatos que fez
- Navegador usado
