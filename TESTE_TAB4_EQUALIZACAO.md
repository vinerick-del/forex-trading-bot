# 🧪 Guia de Testes - Tab 4: Equalização

## Objetivo
Validar que a funcionalidade completa de equalização de fornecedores está funcionando corretamente, incluindo:
- Seleção de processo
- Adição de propostas
- Adição de itens
- Preenchimento de preços
- Cálculo de melhores preços (green highlighting)
- Resumos por valor, material, prazo e garantia
- Aprovação por diferentes critérios

## Pré-requisitos
- Navegador moderno (Chrome, Firefox, Edge, Safari)
- Arquivo `teste_app.html` aberto

## 📋 Checklist de Testes

### 1️⃣ Setup Inicial (Tab 2: Cadastro Fornecedor)
- [ ] Abra a aplicação em navegador
- [ ] Clique em "🏢 Cadastro Fornecedor" (Tab 2)
- [ ] Cadastre 3 fornecedores:
  - Siemens (SP, email, CNPJ, etc.)
  - ABB (RJ, email, CNPJ, etc.)
  - Schneider (MG, email, CNPJ, etc.)
- [ ] Clique "✓ Cadastrar Fornecedor" para cada um
- [ ] Verifique notificação de sucesso

### 2️⃣ Criar Novo Processo (Tab 1)
- [ ] Clique em "➕ Novo Processo" (Tab 1)
- [ ] Preencha:
  - Número DATAGED: `DG-2025-001`
  - Descrição: `Cabos e Transformadores Q1`
  - Centro de Custo: `CC-001`
  - Responsável: `João Silva`
  - Tipo: `Cabos`
- [ ] Clique "Criar Processo"
- [ ] Verifique se redireciona para Cotação

### 3️⃣ Acessar Tab 4 - Equalização
- [ ] Clique em "⚖️ Equalização" (Tab 4)
- [ ] Verifique dropdown "Selecione o Processo DATAGED"
- [ ] Selecione o processo criado (`DG-2025-001`)
- [ ] Verifique se `equalizacao-container` aparece
- [ ] Verifique dados básicos exibindo DATAGED e Responsável

### 4️⃣ Adicionar Propostas
- [ ] Clique botão "+ Adicionar Proposta"
- [ ] Verifique se proposta é adicionada
- [ ] Clique botão "+ Adicionar Proposta" 2 vezes mais
- [ ] Total deve estar 3 (uma por fornecedor)
- [ ] Verificar se contadores atualizaram: "Fornecedores: 3"
- [ ] Verifique notificação de sucesso

### 5️⃣ Associar Fornecedores a Propostas
- [ ] Na tabela, clique no dropdown de fornecedor da 1ª coluna
- [ ] Selecione "SIEMENS"
- [ ] Clique no dropdown da 2ª coluna
- [ ] Selecione "ABB"
- [ ] Clique no dropdown da 3ª coluna
- [ ] Selecione "SCHNEIDER"
- [ ] Verifique que nomes dos fornecedores aparecem no cabeçalho das colunas
- [ ] Verifique que propostas foram salvas em localStorage

### 6️⃣ Adicionar Itens
- [ ] Clique botão "+ Adicionar Item"
- [ ] Verifique se linha vazia aparece na tabela
- [ ] Preenchaunha:
  - Tipo: `Cabo Elétrico`
  - Código: `100101`
  - Descrição: `Cabo 10mm² cobre isolado`
  - Qtd: `100`
- [ ] Clique botão "+ Adicionar Item" novamente
- [ ] Preencha:
  - Tipo: `Transformador`
  - Código: `100205`
  - Descrição: `Transformador 500KVA`
  - Qtd: `2`
- [ ] Verifique contador: "Itens: 2"
- [ ] Verifique notificações de sucesso

### 7️⃣ Preencher Preços
- [ ] Preencha preços para Cabo (100101) para cada fornecedor:
  - Siemens: `9.50`
  - ABB: `10.00`
  - Schneider: `9.80`
- [ ] Verifique totais calculam automaticamente:
  - Siemens: `950.00` (9.50 × 100)
  - ABB: `1000.00` (10.00 × 100)
  - Schneider: `980.00` (9.80 × 100)
- [ ] Verifique que a linha de Siemens fica com background verde (#dcfce7)
- [ ] Clique Tab ou Enter para confirmar entrada
- [ ] Verifique que resumo se atualiza automaticamente

### 8️⃣ Testar Green Highlighting (Melhor Preço)
- [ ] Para Transformador (100205), preencha:
  - Siemens: `145.00`
  - ABB: `150.00`
  - Schneider: `145.50`
- [ ] Totais devem ser:
  - Siemens: `290.00` (145.00 × 2)
  - ABB: `300.00` (150.00 × 2)
  - Schneider: `291.00` (145.50 × 2)
- [ ] Verifique que Siemens fica verde (melhor preço)

### 9️⃣ Verificar Resumo por Valor
- [ ] Desça até "💰 Resumo por Fornecedor"
- [ ] Verifique valores totais por fornecedor:
  - Siemens: R$ 1.240,00 (melhor = verde)
  - ABB: R$ 1.300,00
  - Schneider: R$ 1.271,00
- [ ] Verifique que Siemens tem ✓ green indicator

### 🔟 Verificar Resumo por Material
- [ ] Verifique "📦 Melhor Preço por Material"
- [ ] Deve mostrar:
  - 100101: SIEMENS - R$ 9,50 ✓
  - 100205: SIEMENS - R$ 145,00 ✓

### 1️⃣1️⃣ Verificar Resumo por Prazo
- [ ] Verifique "⏱️ Resumo por Prazo"
- [ ] Deve listar os fornecedores com "-" (não preenchidos)
- [ ] Clique em um campo de preço e procure campos de prazo na proposta (se houver)

### 1️⃣2️⃣ Verificar Resumo por Garantia
- [ ] Verifique "🛡️ Resumo por Garantia"
- [ ] Deve listar os fornecedores com "-" (não preenchidos)

### 1️⃣3️⃣ Testar Aprovação por Melhor Preço
- [ ] Clique botão "💰 Melhor Preço"
- [ ] Verifique alerta mostrando: "✓ Aprovado: SIEMENS - R$ 1.240,00"
- [ ] Clique OK
- [ ] Verifique notificação de "Equalização salva"

### 1️⃣4️⃣ Testar Salvamento em localStorage
- [ ] Abra DevTools (F12)
- [ ] Vá para Application → localStorage
- [ ] Procure por chave `processos_amazon`
- [ ] Verifique se contém propostas com fornecedorId e itens com precoUnitario

### 1️⃣5️⃣ Testar Recarregamento
- [ ] Pressione Ctrl+R para recarregar página
- [ ] Clique em "⚖️ Equalização"
- [ ] Selecione processo `DG-2025-001` novamente
- [ ] Verifique se todos os dados (propostas, itens, preços) persistem
- [ ] Verifique que resumos se recalculam corretamente

### 1️⃣6️⃣ Testar Caso de Sem Preços Preenchidos
- [ ] Clique "+ Adicionar Item"
- [ ] Preencha sem adicionar preços:
  - Tipo: `Disjuntor`
  - Código: `100310`
  - Descrição: `Disjuntor 63A`
  - Qtd: `1`
- [ ] Verifique que resumo por material mostra "Sem preços preenchidos"
- [ ] Verifique que green highlighting não aparece

### 1️⃣7️⃣ Testar Mudança de Preço
- [ ] Altere preço de um item (ex: Siemens - Cabo de 9.50 para 8.50)
- [ ] Verifique que:
  - Total recalcula (850.00)
  - Green highlighting muda para Siemens
  - Resumo por Valor se atualiza
  - localStorage é atualizado

### 1️⃣8️⃣ Testar Mudança de Fornecedor na Proposta
- [ ] Clique dropdown de fornecedor (coluna Siemens)
- [ ] Selecione fornecedor diferente (ex: ABB)
- [ ] Verifique que:
  - Cabeçalho da coluna muda
  - Resumo por Valor recalcula
  - localStorage é atualizado

## ✅ Critérios de Sucesso

- ✓ Todos os botões funcionam sem erros
- ✓ Dados persistem em localStorage
- ✓ Green highlighting aparece corretamente para melhor preço
- ✓ Resumos calculam corretamente
- ✓ Notificações aparecem quando apropriado
- ✓ Nenhum erro no console (F12 → Console)
- ✓ Tabela renderiza com todas as colunas

## 🐛 Se Encontrar Problemas

### Dropdown vazio
```javascript
// No console:
console.log(state.processos);
console.log(state.fornecedores);
```

### Preços não calculam
- Verifique se quantidade está preenchida
- Verifique se preço unitário é número válido

### localStorage não funciona
- Verifique permissões do navegador
- Limpe cache (Ctrl+Shift+Del)
- Verifique se localStorage está habilitado

### Green highlighting errado
- Verifique console para erros em Math.min()
- Verifique se preços estão sendo gravados corretamente

## 📊 Dados Esperados

### Após teste completo, localStorage deve conter:

```javascript
{
  "processos_amazon": [
    {
      "dataged": "DG-2025-001",
      "descricao": "Cabos e Transformadores Q1",
      "propostas": [
        {
          "id": <timestamp>,
          "numeroCotacao": "COT-1",
          "fornecedorId": <id-siemens>,
          "itens": [
            {
              "tipoMaterial": "Cabo Elétrico",
              "codigo": "100101",
              "quantidade": 100,
              "precoUnitario": 9.50
            },
            {
              "tipoMaterial": "Transformador",
              "codigo": "100205",
              "quantidade": 2,
              "precoUnitario": 145.00
            }
          ]
        },
        // ... outras propostas
      ]
    }
  ]
}
```

---

**Status**: 📋 Testes Definidos
**Próximo**: Executar testes e reportar resultados
**Tempo Estimado**: 15-20 minutos
