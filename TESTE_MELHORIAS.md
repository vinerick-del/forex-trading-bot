# ⚡ Quick Test - Melhorias Tab 4

**Tempo**: 5 minutos  
**Objetivo**: Validar as 5 melhorias implementadas

---

## 🚀 Setup Rápido (1 min)

```
1. Abra teste_app.html
2. Tab 2 → Cadastre 2 fornecedores:
   - SIEMENS (SP)
   - ABB (RJ)
3. Tab 1 → Crie processo DG-2026-001
4. Tab 4 → Selecione o processo
```

---

## 🧪 5 Testes Principais

### ✅ Teste 1: Condições Colapsáveis (1 min)

```
1. Clique "+ Adicionar Proposta" (2 vezes)
2. Selecione SIEMENS na primeira
3. Selecione ABB na segunda

Esperado:
✅ Nome fornecedor visível
✅ Botão ▶ (triângulo apontando direita)
✅ Campos de prazo/pagamento OCULTOS

4. Clique ▶ na coluna SIEMENS

Esperado:
✅ ▶ vira ▼
✅ Aparecem campos: Prazo, Pagamento, Frete, Garantia

5. Clique ▼ para colapsar novamente

Esperado:
✅ ▼ vira ▶
✅ Campos desaparecem
```

---

### ✅ Teste 2: Excluir Proposta (1 min)

```
1. Clique botão ✕ VERMELHO ao lado de ▶ (SIEMENS)

Esperado:
✅ Alert: "Tem certeza que deseja excluir esta proposta?"

2. Clique OK

Esperado:
✅ Coluna SIEMENS desaparece
✅ Só fica ABB
✅ Notificação: "✓ Proposta excluída"
✅ Contador muda: "Fornecedores: 1"
```

---

### ✅ Teste 3: Excluir Item (1 min)

```
1. Clique "+ Adicionar Item"
2. Preencha:
   - Tipo: Cabo
   - Código: 100101
   - Descrição: Teste
   - Qtd: 100

3. Na linha do item, coluna mais à direita
4. Clique botão ✕ VERMELHO

Esperado:
✅ Alert: "Tem certeza que deseja excluir este item?"

5. Clique OK

Esperado:
✅ Linha desaparece
✅ Notificação: "✓ Item excluído"
✅ Contador muda: "Itens: 0"
```

---

### ✅ Teste 4: Fornecedor Invisível (1 min)

```
1. Clique "+ Adicionar Proposta"

Esperado:
❌ Proposta NÃO aparece na matriz ainda
❌ Não entra no contador de fornecedores
(porque não tem fornecedor definido)

2. Selecione fornecedor (ex: SIEMENS)

Esperado:
✅ Proposta APARECE na matriz
✅ Contador atualiza
✅ Aparece em resumos
```

---

### ✅ Teste 5: Sem IPI/PIS (1 min)

```
1. Clique "+ Adicionar Proposta" + SIEMENS
2. Clique "+ Adicionar Item" com dados
3. Preencha preço: 100.00

Esperado na coluna SIEMENS:
✅ Subtotal: R$ XXX
✅ DIFAL: R$ YYY (se interestadual)
✅ TOTAL: R$ ZZZ

❌ NÃO deve aparecer:
❌ IPI (0%)
❌ PIS/COFINS
```

---

### ✅ Teste 6: Sem Matriz de Risco (1 min)

```
1. Desça até "⚠️ Análise de Riscos"

Esperado:
✅ Vê 3 caixas: Preço, Equilíbrio, Prazo
❌ NÃO vê tabela: "📊 Matriz de Riscos"
```

---

## ✅ Checklist Final

- [ ] Collapse/expand funciona (▶/▼)
- [ ] Botão delete proposta funciona
- [ ] Botão delete item funciona
- [ ] Proposta sem fornecedor fica invisível
- [ ] Proposta com fornecedor aparece
- [ ] IPI não aparece na coluna
- [ ] PIS/COFINS não aparece na coluna
- [ ] Matriz de risco desapareceu
- [ ] Análise de riscos ainda mostra 3 cenários
- [ ] Notificações aparecem após delete

---

## 🎯 Se Algo Falhar

### Collapse não funciona?
- DevTools (F12) → Console
- Procure por erro em vermelho
- Recarregue página: Ctrl+R

### Não consigo deletar?
- Certifique que clicou no ✕ correto
- Confirme o alert que aparece
- Verifique localStorage (F12 → Application)

### Propostas sem fornecedor ainda aparecem?
- Recarregue página
- Limpe cache (Ctrl+Shift+Del)
- Clique em Tab 4 novamente

### Tabelas com layout estranho?
- Expanda/collapse as condições
- Redimensione janela
- Teste em tela cheia (F11)

---

## 📊 Resultado Esperado

Após todos os testes:
- ✅ Interface mais limpa
- ✅ Menos cliques para usar
- ✅ Nenhuma informação confusa (IPI=0)
- ✅ Fácil gerenciar erros (delete)
- ✅ Apenas dados válidos aparecem

---

**Documentação Completa**: MELHORIAS_VISUAL_TAB4.md  
**Commit**: 111b28e  
**Tempo Estimado**: 5 minutos  
