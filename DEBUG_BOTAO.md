# 🔍 Debug - Botão "+ Adicionar Proposta" Inativo

## O Problema

O botão **pode estar funcionando**, mas a proposta criada **não fica visível** porque:

1. A proposta é criada com `fornecedorId: null`
2. A tabela comparativa FILTRA apenas propostas com `fornecedorId` definido
3. Usuário não vê a proposta na tabela e pensa que o botão não funcionou

---

## 🧪 Como Verificar Se O Botão Está Funcionando

### Passo 1: Abra DevTools (F12)
```
1. Clique F12
2. Vá para tab "Console"
```

### Passo 2: Crie um Processo e Carregue Tab 4
```
1. Clique Tab 1 "➕ Novo Processo"
2. Preencha:
   - DATAGED: TEST-001
   - Descrição: Teste Debug
   - Centro Custo: CC-001
   - Responsável: Seu Nome
   - Tipo: Cabos
3. Clique "Criar Processo"
4. Vá para Tab 4 "⚖️ Equalizacão"
5. No dropdown, selecione "TEST-001"
✅ Container deve aparecer com os botões
```

### Passo 3: Clique "+ Adicionar Proposta" e Verifique no Console
```
1. NO CONSOLE (F12), digite:
   state.processoAtual.propostas.length

2. Anote o número (ex: 0)

3. Clique "+ Adicionar Proposta"

4. NO CONSOLE, digite NOVAMENTE:
   state.processoAtual.propostas.length

5. Se o número AUMENTOU, o botão FUNCIONOU ✓
6. Se o número ficou igual, o botão NÃO FUNCIONOU ✗
```

### Passo 4: Verifique A Proposta Criada
```
1. NO CONSOLE, digite:
   state.processoAtual.propostas[0]

2. Você verá um objeto com:
   - id: xxxxxxxx
   - numeroCotacao: "COT-1"
   - fornecedorId: null  ← AQUI!
   - prazoEntrega: null
   - prazoPagamento: null
   - tipoFrete: "CIF"
   - garantiasMeses: null
   - itens: []

3. ✅ Se vê tudo isso, o botão CRIOU A PROPOSTA CORRETAMENTE
```

### Passo 5: Entender Por Que Não Aparece Na Tabela
```
1. Clique "Tab 2 🏢 Cadastro Fornecedor"
2. Cadastre:
   - Nome: TESTE
   - Email: teste@test.com
   - CNPJ: 12.345.678/0001-90
   - Telefone: 1133334444
   - UF: SP
   - Cidade: São Paulo
3. Clique "✓ Cadastrar Fornecedor"
4. Volte para Tab 4
5. Selecione novamente o processo "TEST-001"
```

### Passo 6: Agora Selecione Um Fornecedor
```
1. Na tabela, há um DROPDOWN dizendo "Selecione fornecedor"
   ❌ Ele está VAZIO = proposta invisível

2. Clique no dropdown
3. Selecione "TESTE"
4. ✅ AGORA a coluna deve ficar VISÍVEL!
```

---

## 📋 Resultado Esperado

### Se o botão FUNCIONA:
```
1. Clique "+ Adicionar Proposta"
   ✓ Notificação: "✓ Proposta adicionada"
   ✓ state.processoAtual.propostas.length aumenta
   ✓ Proposta é criada (sem ser visível)

2. Selecione fornecedor no dropdown
   ✓ Proposta APARECE na tabela
   ✓ Coluna do fornecedor fica visível
```

### Se o botão NÃO FUNCIONA:
```
1. Clique "+ Adicionar Proposta"
   ✗ Nada acontece
   ✗ state.processoAtual.propostas.length NÃO muda
   ✗ Nenhuma notificação aparece
   ✗ Console mostra erro em vermelho
```

---

## 🔧 Se O Botão NÃO Funciona (Diagnóstico)

### Abra o Console (F12 → Console)
```
1. Procure por ERRO EM VERMELHO
2. Copie a mensagem de erro completa
3. Digite também:
   typeof adicionarPropostaEqualizacao
   
   Se responder "function" = função existe ✓
   Se responder "undefined" = função NÃO foi carregada ✗
```

### Tente Chamar a Função Manualmente
```
1. NO CONSOLE, digite:
   adicionarPropostaEqualizacao()

2. Se funciona, o botão deveria ter funcionado também
3. Se der erro, há um problema no código
```

### Verifique Se O Container Está Visível
```
1. NO CONSOLE, digite:
   document.getElementById('equalizacao-container').style.display

2. Se responder "block" = container está VISÍVEL ✓
3. Se responder "none" = container está OCULTO ✗
   (Você precisa selecionar um processo no dropdown primeiro)
```

---

## ✅ Conclusão

O problema **provavelmente é**:
1. Botão ESTÁ funcionando
2. Proposta É criada (invisível porque sem fornecedor)
3. Usuário não vê a proposta e pensa que falhou

**Solução**: Selecione um fornecedor no dropdown da proposta para vê-la aparecer na tabela.

---

**Se depois desses testes o botão continuar não funcionando, copie:**
- Screenshot do erro no console
- Resultado de `state.processoAtual.propostas.length`
- Mensagem de erro completa (se houver)

E reporte o problema com esses detalhes.
