# 📊 Mapa de Equalização - Estrutura Completa

## Interface em 3 Partes

### 1️⃣ DADOS BÁSICOS E ESCOPO

```
┌──────────────────────────────────────────────────────────────────┐
│ 📋 DADOS BÁSICOS E ESCOPO                                       │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│ Número da Cotação: [COT-001          ]  Data: [2025-05-22]      │
│                                                                  │
│ Responsável: [João Silva         ]  Fornecedor: [Siemens ▼]    │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### 2️⃣ TABELA RESUMIDA - VISÃO GERAL DE TODOS OS ITENS

```
┌────┬───────┬──────────────┬────┬───────┬─────────┬────────┬────────┬────────┬─────────┐
│ # │ Tipo* │  Código *    │Und*│ Qtd * │ Preço $ │ ICMS % │ Frete  │ TCO    │ Score  │
├────┼───────┼──────────────┼────┼───────┼─────────┼────────┼────────┼────────┼─────────┤
│01 │[Cabo] │[100101     ] │[m] │[100] │ R$ 9.50 │ 18%   │ R$ 5.00│ R$ 0  │ 4.2/5  │
│02 │[Disj] │[100205     ] │[un]│[ 2 ] │ R$ 145  │ 18%   │ R$ 2.00│ R$ 0  │ 3.8/5  │
│03 │[Tran] │[100312     ] │[un]│[ 1 ] │ R$ 4200 │ 18%   │ R$ 0  │ R$ 0  │ 4.5/5  │
│   │[+Item]│               │    │      │         │        │        │        │        │
└────┴───────┴──────────────┴────┴───────┴─────────┴────────┴────────┴────────┴─────────┘
```

### 3️⃣ DETALHES DO ITEM (AO CLICAR)

Abre expansão ou modal com todos os campos:

```
┌────────────────────────────────────────────────────────────────┐
│ ITEM 01: CABO ELÉTRICO                                         │
├─ ESPECIFICAÇÃO TÉCNICA ──────────────────────────────────────┤
│ Tipo de Material: [Cabo Elétrico             ]                │
│ Código SAP: [100101                ]                          │
│ Descrição: [Cabo 10mm² cobre isolado PVC    ]                │
│ Unidade: [m         ]  Quantidade: [100    ]                │
│                                                                │
├─ CUSTOS E FORMAÇÃO DE PREÇO ─────────────────────────────────┤
│ Preço Unitário: [9.50] = Total: R$ 950,00                   │
│ ICMS: [18]% = R$ 171,00                                      │
│ IPI: [0]% = R$ 0,00                                          │
│ PIS/COFINS: [7.65]% = R$ 72,68                               │
│ Frete: [5.00] Incoterm: [CIF / FOB / CIF]                   │
│ TCO (Manutenção/Garantia/Ano): [0,00]                        │
│                                                                │
├─ CONDIÇÕES COMERCIAIS E PRAZOS ──────────────────────────────┤
│ Condição Pagamento: [30 dias   ]                              │
│ Prazo Entrega: [15 dias        ]                              │
│ Validade Proposta: [2025-06-22 ]                              │
│                                                                │
├─ CRITÉRIOS DE QUALIDADE E RISCO ────────────────────────────┤
│ Garantia: [12 meses            ]                              │
│ Compliance: [✓ Sim / ✗ Não]                                  │
│                                                                │
├─ NOTAS DE AVALIAÇÃO (0-5) ──────────────────────────────────┤
│ Especificação Técnica: [4] ⭐⭐⭐⭐                        │
│ Prazo de Entrega: [5] ⭐⭐⭐⭐⭐                       │
│ Qualidade/Conformidade: [4] ⭐⭐⭐⭐                    │
│ Reputação/Histórico: [4] ⭐⭐⭐⭐                       │
│                                                                │
│ NOTA FINAL (Custo-Benefício): [4.2/5] ⭐⭐⭐⭐          │
│                                                                │
│ [Editar] [Clonar] [Remover] [Fechar]                         │
└────────────────────────────────────────────────────────────────┘
```

---

## 📋 Campos Detalhados

### 🏷️ DADOS BÁSICOS E ESCOPO (Topo)

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| Número Cotação | Text | ✓ | Ex: COT-001, COT-2025-0001 |
| Data Cotação | Date | ✓ | Data de emissão |
| Responsável Compra | Text | ✓ | Nome do comprador |
| Fornecedor | Select | ✓ | Dropdown com fornecedores cadastrados |

### 📦 ESPECIFICAÇÃO TÉCNICA (Item)

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| # Item | Number | Auto | 01, 02, 03... |
| Tipo de Material | Text | ✓ | LIVRE - ex: "Cabo", "Disjuntor", "Transformador" |
| Código SAP | Text | ✓ | Código do material |
| Descrição | Text | ✓ | Descrição detalhada |
| Unidade | Text | ✓ | m, un, kg, cx, etc |
| Quantidade | Number | ✓ | Quantidade solicitada |

### 💰 CUSTOS E FORMAÇÃO DE PREÇO (Item)

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| Preço Unitário | Decimal | ✓ | Valor por unidade |
| Preço Total | Decimal | Auto | Quantidade × Preço Unitário |
| ICMS % | Decimal | - | Imposto estadual (0-100) |
| ICMS Valor | Decimal | Auto | Calcula automaticamente |
| IPI % | Decimal | - | Imposto federal (0-100) |
| IPI Valor | Decimal | Auto | Calcula automaticamente |
| PIS/COFINS % | Decimal | - | (0-100), geralmente 7.65% |
| PIS/COFINS Valor | Decimal | Auto | Calcula automaticamente |
| Frete | Decimal | - | Custo de frete |
| Incoterm | Select | - | CIF, FOB, DDP, EXW, etc |
| TCO Anual | Decimal | - | Total Cost of Ownership (manutenção, garantia/ano) |

### 🤝 CONDIÇÕES COMERCIAIS E PRAZOS (Item)

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| Condição Pagamento | Select | - | À vista, 15d, 30d, 45d, 60d, 90d |
| Prazo Entrega (Lead Time) | Number | - | Dias entre pedido e entrega |
| Validade Proposta | Date | - | Até quando o preço é válido |

### ✅ CRITÉRIOS DE QUALIDADE E RISCO (Item)

| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| Garantia | Select | - | 3m, 6m, 12m, 24m, 36m, Sem |
| Compliance | Radio | - | Sim / Não (normas, licenças) |

### ⭐ NOTAS DE AVALIAÇÃO (Item)

Cada uma de 0-5 (show stars):

| Campo | Descrição |
|-------|-----------|
| Especificação Técnica | Atende 100% às especificações? |
| Prazo de Entrega | Prazo viável e competitivo? |
| Qualidade/Conformidade | Marca confiável, certificações? |
| Reputação/Histórico | Histórico de entregas do fornecedor |

**Cálculo Automático:**
```
Nota Final = (Esp.Técnica + Prazo + Qualidade + Reputação) / 4
```

---

## 🎯 Fluxo de Uso

1. **Selecionar Processo** → Lista de propostas
2. **Preencher Dados Básicos** (topo)
3. **Adicionar Itens** com [+ Item]
4. **Preencher Campos Resumidos** na tabela
5. **Clicar em Item** para expandir e editar detalhes
6. **Scores Calculam Automaticamente**
7. **[Salvar]** para persistir

---

## 💾 Estrutura de Dados

```javascript
state.processos[].propostas = [
  {
    id: 1234567890,
    numeroCotacao: "COT-001",
    dataCotacao: "2025-05-22",
    responsavelCompra: "João Silva",
    fornecedorId: 456,  // Referência ao fornecedor
    
    itens: [
      {
        numero: 1,
        tipoMaterial: "Cabo Elétrico",
        codigo: "100101",
        descricao: "Cabo 10mm² cobre isolado",
        unidade: "m",
        quantidade: 100,
        precoUnitario: 9.50,
        precoTotal: 950.00,
        
        // Impostos
        icms: 18,
        icmsValor: 171.00,
        ipi: 0,
        ipiValor: 0,
        pisCofins: 7.65,
        pisCofinsValor: 72.68,
        
        // Logística
        frete: 5.00,
        incoterm: "CIF",
        tco: 0,
        
        // Comercial
        condicaoPagamento: "30 dias",
        prazoEntrega: 15,
        validadeProposta: "2025-06-22",
        
        // Qualidade
        garantia: "12 meses",
        compliance: true,
        
        // Avaliação
        notas: {
          especificacao: 4,
          prazo: 5,
          qualidade: 4,
          reputacao: 4
        },
        notaFinal: 4.25  // Auto-calculada
      }
    ]
  }
]
```

---

## ✨ Funcionalidades

- ✅ Cálculos automáticos de impostos
- ✅ Total cost of ownership
- ✅ Scores com estrelas
- ✅ Comparação multi-item
- ✅ Dropdown de fornecedores
- ✅ Expansão/colapso de itens
- ✅ Edição inline (tabela) e detalhada (modal)
- ✅ Validações de campos obrigatórios
- ✅ Persistência em localStorage
- ✅ Exportação para PDF/Excel

---

**Status**: 🎯 Estrutura Definida
**Próximo**: Implementação na interface
