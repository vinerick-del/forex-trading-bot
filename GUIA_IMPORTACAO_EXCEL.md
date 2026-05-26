# 📋 Guia de Importação Rápida de Cotações do Excel

## Como Usar a Importação Rápida

### Método 1: Copy-Paste Direto (Recomendado) ✨

**Passo 1:** No seu Excel, selecione as colunas com dados de cotação:
```
Código      | Descrição              | Unidade | Qtd | Valor Unit. | Fabricante
CBN-001     | Cabo de Cobre 10mm²    | UND     | 100 | 50.00       | ABC Inc
TRF-001     | Transformador 100kVA   | UND     | 5   | 1500.00     | XYZ Ltd
```

**Passo 2:** Copie os dados (Ctrl+C)

**Passo 3:** No app:
1. Acesse a aba **💰 Cotações**
2. Selecione uma **Requisição**
3. Selecione o **Fornecedor**
4. Cole os dados no campo **"Cole os dados aqui"** (Ctrl+V)
5. Clique em **"📥 Importar do Excel"**

✅ Pronto! As cotações serão importadas automaticamente.

---

### Formato de Dados Suportados

#### **Formato A: Separado por Abas (Excel Copy-Paste)**
```
CBN-001	Cabo de Cobre 10mm²	UND	100	50.00	ABC Inc
TRF-001	Transformador 100kVA	UND	5	1500.00	XYZ Ltd
DSJ-001	Disjuntor Bipolar 40A	UND	50	200.00	ABC Inc
```

**Colunas na ordem:**
1. **Código** (obrigatório)
2. **Descrição** (obrigatório)
3. **Unidade** (opcional - padrão: UND)
4. **Quantidade** (obrigatório)
5. **Valor Unitário** (obrigatório)
6. **Fabricante** (opcional)

#### **Formato B: Uma Coluna por Linha**
```
CBN-001
Cabo de Cobre 10mm²
UND
100
50.00
ABC Inc

TRF-001
Transformador 100kVA
UND
5
1500.00
XYZ Ltd
```

---

## 🎯 Exemplos de Uso

### Exemplo 1: Importar 3 Cotações
**Excel:**
```
CBN-001	Cabo 10mm²	UND	100	50.00	ABC Inc
TRF-001	Transformador	UN	5	1500.00	XYZ
DSJ-001	Disjuntor 40A	UN	50	200.00	ABC Inc
```

**Resultado:** ✅ 3 cotações importadas com sucesso

### Exemplo 2: Importar com Dados Incompletos
**Excel:**
```
CBN-001	Cabo 10mm²	UND	100	50.00
TRF-001	Transformador			1500.00	XYZ
DSJ-001	Disjuntor 40A	UN	50	200.00
```

**Resultado:** 
- ✅ CBN-001: Importada (fabricante vazio, usa padrão)
- ⚠️ TRF-001: Pulada (Qtd/Valor inválidos)
- ✅ DSJ-001: Importada

---

## ⚙️ Configurações Importantes

### Campos Obrigatórios:
- ✓ **Código** - Identificador do item
- ✓ **Descrição** - Nome do produto
- ✓ **Quantidade** - Número > 0
- ✓ **Valor Unitário** - Número > 0

### Campos Opcionais:
- Unidade (padrão: UND)
- Fabricante

### Formato de Valores Monetários:
```
✅ Correto:  50.00, 1500, 199.99
❌ Errado:   R$ 50,00 (remove R$ e use . não ,)
```

---

## 🔄 Workflow Recomendado

1. **Prepare o Excel:**
   - Crie uma tabela com os dados de cotação
   - Verifique se todos os valores estão corretos
   - Certifique-se de usar . (ponto) para decimais

2. **No App:**
   - Crie a Requisição (📋 Requisição)
   - Cadastre os Fornecedores (🏢 Fornecedores)
   - Acesse Cotações (💰 Cotações)
   - Selecione a Requisição
   - Selecione o Fornecedor
   - Cole e importe dados

3. **Verifique:**
   - Confirme que as cotações foram importadas na tabela
   - Verifique códigos, quantidades e valores
   - Se houver erro, delete a cotação e reimporte

---

## 🚨 Dicas de Troubleshooting

### Problema: "Nenhuma cotação importada"
**Solução:** Verifique:
- Você selecionou uma Requisição?
- Você selecionou um Fornecedor?
- Os dados têm as colunas obrigatórias?
- Use formato com abas (Tab) entre colunas

### Problema: Apenas algumas cotações foram importadas
**Solução:** Verifique a coluna "⚠️ Aviso" que aparecerá mostrando:
- Qual linha teve erro
- Por que foi rejeitada
- Corrija o Excel e reimporte

### Problema: Valores aparecem com formato errado
**Solução:**
- Use . (ponto) para decimais, não , (vírgula)
- Não inclua R$ ou símbolos de moeda
- Exemplo: 1500.50 ✓ | R$ 1.500,50 ✗

---

## 📊 Comparação: Entrada Manual vs Importação

| Aspecto | Manual | Importação |
|---------|--------|-----------|
| **Cotações por minuto** | 5-10 | 100+ |
| **Erro de digitação** | Alto | Mínimo |
| **Tédio** | 😫 | 😊 |
| **Ideal para** | 1-2 itens | 10+ itens |

---

## 💡 Macros Excel (Opcional)

Se você usa Excel frequentemente, crie uma macro para preparar os dados:

```vba
' Cole este código em Tools > Macros > Edit
Sub CopiarParaCotacao()
  Dim arr As Variant
  Dim i As Integer
  
  arr = Selection.Value
  
  ' Copia dados para clipboard (use um add-in como VBA.Clipboard)
  ' Aqui é apenas exemplo - considere usar Power Query no Excel
  
End Sub
```

---

## ✨ Funcionalidades Futuras

- [ ] Importar de arquivo Excel (.xlsx)
- [ ] Importar de Google Sheets
- [ ] Template de Excel pré-formatado para download
- [ ] Validação de duplicação de códigos

---

**Status:** ✅ **PRONTO PARA USO**

Para dúvidas ou problemas, verifique os avisos de importação que aparecem após a importação.
