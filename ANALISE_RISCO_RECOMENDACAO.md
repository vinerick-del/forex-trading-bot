# 📊 Análise de Risco e Recomendação Inteligente - Tab 4 Equalização

## 🎯 Visão Geral

A Tab 4 (Equalização) agora apresenta uma **análise completa de risco operacional** e uma **recomendação inteligente** que considera não apenas o preço, mas também prazo, garantia, condições de pagamento e risco.

---

## 📋 Novidades Implementadas

### 1. **Condições do Fornecedor por Proposta**

Cada proposta agora mostra campos de condições ABAIXO do cabeçalho do fornecedor:

```
┌──────────────────────────────────┐
│ SIEMENS                          │
├──────────────────────────────────┤
│ Selecione Fornecedor: [SIEMENS▼] │
├──────────────────────────────────┤
│ Prazo Entrega (d): [15  ]        │
│ Pagamento (d):     [30  ]        │
│ Frete:             [CIF ▼]       │
│ Garantia (m):      [12  ]        │
└──────────────────────────────────┘
```

**Campos:**
- **Prazo Entrega** (dias): Quanto tempo até receber
- **Prazo Pagamento** (dias): Quantos dias para pagar (financeiro)
- **Tipo de Frete**: CIF (vendedor), FOB (comprador), DDP, EXW
- **Garantia** (meses): Período de garantia do produto

---

### 2. **Tabela de Preços Expandida com Tributos**

Cada célula de fornecedor agora mostra BREAKDOWN completo:

```
┌─────────────────────────────────┐
│ SP (UF Origem)                  │
├─────────────────────────────────┤
│ Preço Unit.: [9.50        ]    │
├─────────────────────────────────┤
│ Subtotal:      R$ 950.00        │
│ IPI (0%):      R$ 0.00          │
│ PIS/COFINS:    R$ 72.68         │
│ ICMS SP: 18%                    │
│ DIFAL:         R$ 104,50        │
├─────────────────────────────────┤
│ TOTAL:         R$ 1.127,18 ✓   │
└─────────────────────────────────┘
```

**Cálculos Automáticos:**
1. **Subtotal** = Preço Unitário × Quantidade
2. **IPI** = Subtotal × Alíquota IPI
3. **PIS/COFINS** = Subtotal × 7,65% (padrão)
4. **ICMS** = Baseado na UF do fornecedor
5. **DIFAL** = (ICMS AM - ICMS Interestadual) × Subtotal
6. **TOTAL = Subtotal + IPI + PIS/COFINS + DIFAL**

---

### 3. **Recomendação Inteligente - Melhor Equilíbrio**

Análise automática que considera:
- **40%** - Preço (custo total com tributos)
- **30%** - Prazo de entrega
- **20%** - Garantia (confiabilidade)
- **10%** - Tipo de frete (CIF/DDP melhor = 10 pontos)

**Exemplo de Recomendação:**
```
✓ RECOMENDADO: ABB

Custo Total:        R$ 15.450,00
Prazo Entrega:      18 dias
Prazo Pagamento:    30 dias
Garantia:           12 meses
Frete:              CIF

Score Equilíbrio:   87.5/100
Risco Operacional:  MÉDIO
└─ ⚠️ Prazo de pagamento longo | ℹ️ Fornecedor em UF distante
```

---

### 4. **Análise de Risco Operacional**

Cada fornecedor recebe uma **pontuação de risco** (0-100):

#### **Fatores de Risco:**

| Fator | Pontos | Descrição |
|-------|--------|-----------|
| Prazo < 7 dias | +15 | Entrega muito rápida = difícil de cumprir |
| Prazo > 30 dias | +10 | Entrega lenta = imobiliza caixa |
| Pagamento > 60 dias | +12 | Longo prazo = risco de crédito |
| Sem garantia | +20 | Sem cobertura = risco de defeito |
| Garantia < 12 meses | +10 | Cobertura insuficiente |
| FOB/EXW | +8 | Frete por conta = responsabilidade |
| UF distante | +5 | Difícil acesso = suporte lento |

#### **Níveis de Risco:**
- **🟢 Baixo** (0-20 pontos): Fornecedor confiável
- **🟡 Médio** (21-35 pontos): Atenção necessária
- **🟠 Alto** (36-50 pontos): Risco significativo
- **🔴 Muito Alto** (51+ pontos): Evitar se possível

---

### 5. **Matriz Comparativa de Riscos**

Três cenários de decisão:

#### **Cenário 1: Escolher pelo PREÇO MAIS BARATO**
```
💰 Risco - Melhor Preço
Fornecedor: SIEMENS
Preço: R$ 15.200,00 (MENOR)
Risco: ALTO
⚠️ Prazo muito curto | Sem garantia | Frete FOB
```

**O que pode dar errado:**
- Produto chega com defeito (sem garantia)
- Não consegue pagar o frete
- Atraso na entrega


#### **Cenário 2: Escolher pelo EQUILÍBRIO (RECOMENDADO)**
```
⚖️ Risco - Melhor Equilíbrio
Fornecedor: ABB
Preço: R$ 15.450,00
Risco: MÉDIO
✓ Risco aceitável com garantia de 12 meses
```

**Benefícios:**
- Melhor custo-benefício
- Garantia cobre defeitos
- Prazo realista


#### **Cenário 3: Escolher pelo PRAZO MAIS CURTO**
```
⏱️ Risco - Prazo Mais Curto
Fornecedor: SCHNEIDER
Prazo: 10 dias
Preço: R$ 15.600,00 (MAIS CARO)
Risco: MÉDIO-ALTO
⚠️ Pode ter maior risco operacional
```

**Problemas:**
- Preço mais alto
- Pode não conseguir cumprir prazo
- Qualidade pode ser afetada

---

## 📊 Exemplo Prático Completo

### Cenário: Compra de 100 unidades de Cabo Elétrico

#### **Fornecedor A - São Paulo (SP)**
```
Preço Unitário: R$ 9.50
Subtotal (100): R$ 950,00
IPI (0%):       R$ 0,00
PIS/COFINS:     R$ 72,68
ICMS SP (18%):  Incluído na base
DIFAL:          R$ 104,50 (interestadual)

TOTAL:          R$ 1.127,18
Prazo:          7 dias (⚠️ muito rápido)
Pagamento:      60 dias (⚠️ caixa)
Garantia:       0 meses (⚠️ sem cobertura)
Frete:          FOB (⚠️ por conta)

RISCO: ALTO (65 pontos)
```

#### **Fornecedor B - Rio de Janeiro (RJ)**
```
Preço Unitário: R$ 9.80
Subtotal (100): R$ 980,00
IPI (0%):       R$ 0,00
PIS/COFINS:     R$ 74,97
ICMS RJ (18%):  Incluído na base
DIFAL:          R$ 107,80 (interestadual)

TOTAL:          R$ 1.162,77
Prazo:          18 dias (✓ realista)
Pagamento:      30 dias (✓ normal)
Garantia:       12 meses (✓ coberta)
Frete:          CIF (✓ por conta deles)

RISCO: MÉDIO (22 pontos) ⭐ RECOMENDADO
Score: 82/100
```

#### **Fornecedor C - Manaus (AM)**
```
Preço Unitário: R$ 9.30
Subtotal (100): R$ 930,00
IPI (0%):       R$ 0,00
PIS/COFINS:     R$ 71,20
ICMS AM (18%):  Incluído na base
DIFAL:          R$ 0,00 (operação interna!)

TOTAL:          R$ 1.001,20 ← MENOR PREÇO
Prazo:          20 dias (✓ realista)
Pagamento:      30 dias (✓ normal)
Garantia:       6 meses (⚠️ curta)
Frete:          CIF (✓ por conta deles)

RISCO: BAIXO (10 pontos)
Score: 89/100 ⭐ MELHOR EQUILÍBRIO
```

---

## 🎯 Como Usar a Análise

### Passo 1: Preencher Condições do Fornecedor
- Abra Tab 4 (Equalização)
- Preencha os campos de Prazo, Frete, Garantia para cada proposta

### Passo 2: Ver Recomendação
- Desça até a seção **"🎯 Recomendação Equilibrada"**
- Veja qual fornecedor tem melhor score
- Leia os detalhes e riscos

### Passo 3: Analisar Riscos
- Desça até **"⚠️ Análise de Riscos"**
- Veja os três cenários (preço vs equilíbrio vs prazo)
- Analise a matriz de riscos

### Passo 4: Tomar Decisão
- Se seguir recomendação: clique **"⚖️ Recomendação"** (novo botão)
- Se escolher por preço: clique **"💰 Melhor Preço"**
- Se escolher por prazo: clique **"⏱️ Melhor Prazo"**
- Ou **"👤 Aprovação Manual"**

---

## ⚠️ Interpretando o Risco

### **Exemplo de Alto Risco (65 pontos)**
```
Prazo muito curto (7 dias):  +15
Sem garantia:               +20
Pagamento longo (60 d):     +12
Frete FOB:                   +8
UF distante:                +10
────────────────────────────
TOTAL:                       65 ← ALTO RISCO
```

**Decisão:** Considere outro fornecedor, a menos que não tenha alternativa.

---

### **Exemplo de Risco Aceitável (22 pontos)**
```
Prazo normal (18 dias):       0
Garantia 12 meses:            0
Pagamento 30 dias:            0
Frete CIF:                    0
UF próxima:                   0
Prazo pagamento ok:           0
────────────────────────────
TOTAL:                       22 ← MÉDIO-BAIXO (ACEITÁVEL)

+ Melhor preço relativo:    +10 (bonus score)
─────────────────────────────
SCORE EQUILÍBRIO:           82/100 ← BOA ESCOLHA
```

**Decisão:** Seguro proceder com este fornecedor.

---

## 📈 Score de Equilíbrio

### Fórmula:
```
Score = (Preço_Score × 40%) + (Prazo_Score × 30%) + 
         (Garantia_Score × 20%) + (Frete_Score × 10%)

Máximo: 100 pontos
```

### Interpretação:
- **90-100**: Excelente escolha
- **80-89**: Boa escolha (RECOMENDADO)
- **70-79**: Aceitável
- **60-69**: Marginal (verificar riscos)
- **< 60**: Evitar

---

## 🚨 Casos de Uso

### Caso 1: **Compra Urgente**
- Escolher pelo **prazo mais curto** (mesmo com risco)
- Mas verificar risco operacional
- Considerar seguros/garantias adicionais

### Caso 2: **Orçamento Apertado**
- Considerar **preço mais barato**
- MAS também verificar risco
- Se risco alto: negociar termo + garantia

### Caso 3: **Operação Crítica**
- Seguir **recomendação de equilíbrio**
- Priorizar fornecedor com RISCO BAIXO
- Mesmo que custo seja ligeiramente mais alto

### Caso 4: **Fornecedor Conhecido**
- Se já trabalhou bem com fornecedor
- Risco pode ser reduzido (histórico bom)
- Confiar em histórico de qualidade

---

## 💡 Dicas Importantes

### ✅ Boas Práticas
1. **Nunca escolha APENAS por preço**
   - Análise sempre recomendação + risco

2. **Considere risco operacional**
   - Prazo impossível de cumprir?
   - Sem cobertura pós-venda?

3. **Valide garantia e frete**
   - CIF/DDP melhor (vendedor paga)
   - FOB/EXW pior (você paga)

4. **Equilibre preço e confiabilidade**
   - 5-10% a mais = tranquilidade

### ❌ Erros Comuns
1. Escolher apenas pelo menor preço
2. Ignorar prazo de entrega
3. Confiar em fornecedores sem garantia
4. Não considerar risco de crédito (pagamento)
5. Esquecer custo total (tributos) no preço

---

## 🔄 Quando Recalcular

Clique em um campo e o sistema automaticamente **recalcula**:
- ✓ Preço unitário
- ✓ Prazo entrega
- ✓ Prazo pagamento
- ✓ Tipo frete
- ✓ Garantia meses

**Resultado:** Recomendação e análise se atualizam em tempo real.

---

## 📊 Matriz de Risco Completa

```
FORNECEDOR    PREÇO         RISCO         PONTOS
─────────────────────────────────────────────────
SIEMENS       R$ 15.200     ALTO 🔴       65
ABB           R$ 15.450     MÉDIO 🟡      22 ⭐
SCHNEIDER     R$ 15.600     BAIXO 🟢      10
```

**Decisão Recomendada:** ABB (melhor equilíbrio)

---

## 🎓 Próximas Implementações

- [ ] Histórico de fornecedor (reduz risco)
- [ ] Alertas automáticos de risco muito alto
- [ ] Benchmark de mercado (comparar preços)
- [ ] Scoring de fornecedores (mantém histórico)
- [ ] Simulação "what-if" (mudar termos)

---

**Status**: ✅ Implementado e Funcional
**Data**: 25 de Maio de 2026
**Versão**: 2.0 (Com Análise de Risco)
**Próximo**: Validar com dados reais e ajustar ponderações

