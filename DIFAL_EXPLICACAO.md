# 💰 DIFAL - Diferencial de Alíquota do ICMS

## O que é DIFAL?

DIFAL é o **Diferencial de Alíquota do ICMS**, um mecanismo de cobrança nas operações **interestaduais** com consumidor final não-contribuinte de ICMS.

### Objetivo
Uniformizar a carga tributária de ICMS nas operações interestaduais, evitando concorrência fiscal predatória entre estados.

---

## Cálculo do DIFAL

### Fórmula Básica
```
DIFAL = (ICMS Destino - ICMS Interestadual) × Base de Cálculo
```

### Componentes

| Componente | Descrição | Exemplo |
|-----------|-----------|---------|
| **ICMS Destino** | Alíquota interna do estado final (AM = 18%) | 18% |
| **ICMS Interestadual** | Alíquota federal para operações interestaduais | 7% (padrão) |
| **Base de Cálculo** | Valor do item (Preço × Quantidade) | R$ 950 |
| **DIFAL** | Diferença a ser recolhida | (18% - 7%) × 950 = R$ 104,50 |

---

## Implementação na Âmbar ENERGIA

### 1. Dados de Entrada

#### Tabela de Alíquotas ICMS por UF (2025)

```javascript
const ALIQUOTAS_ICMS = {
  'SP': 18, 'RJ': 18, 'MG': 18, 'RS': 18,  // 18%
  'BA': 18, 'CE': 18, 'PE': 17, 'DF': 18,  // Variados
  'GO': 15, 'MT': 15, 'MS': 15, 'TO': 15,  // 15%
  'AM': 18, // Manaus (Manaus Free Trade Zone pode ter exceções)
  // ... demais UFs
};
```

#### Dados da Empresa Compradora
```javascript
const UF_COMPRADORA = 'AM';           // Manaus, Amazonas
const ALIQUOTA_COMPRADORA = 18;       // ICMS AM = 18%
const ALIQUOTA_INTERESTADUAL = 7;     // Padrão federal
```

#### Dados do Fornecedor
- **UF**: Selecionado no cadastro (Tab 2)
- **Alíquota Origem**: Obtida automaticamente da tabela

---

### 2. Cálculo Automático por Item

Para cada item na tabela de equalização:

```javascript
function calcularDIFAL(ufOrigem, baseCalculo) {
  const icmsOrigem = ALIQUOTAS_ICMS[ufOrigem];     // Ex: SP = 18%
  const icmsDestino = 18;                           // AM = 18%

  let difal = 0;

  if (ufOrigem !== 'AM') {  // Operação interestadual
    const aliquotaDiferencial = icmsDestino - ALIQUOTA_INTERESTADUAL;
    difal = (baseCalculo * aliquotaDiferencial) / 100;
  }
  // Se UF origem = AM: DIFAL = 0 (operação interna)

  return { difal, icmsOrigem, icmsDestino };
}
```

---

### 3. Exibição na Tabela

Para cada fornecedor e item, a tabela mostra:

```
┌─────────────────────────────────────┐
│ SP (UF Origem)                      │
├─────────────────────────────────────┤
│ R$ 9.50 (Preço Unitário)            │
│ Subtotal: R$ 950.00 (100 × 9.50)    │
│ ICMS SP: 18%                        │
│ DIFAL: R$ 104,50                    │
│ Total: R$ 1.054,50 ← INCLUINDO DIFAL│
└─────────────────────────────────────┘
```

### Cores Visuais
- **Verde**: Melhor preço (incluindo DIFAL)
- **Amarelo**: Aviso (DIFAL aplicado - operação interestadual)
- **Verde claro**: Operação interna (DIFAL = 0)

---

### 4. Resumos da Equalização

#### Resumo por Valor (INCLUINDO DIFAL)
```
SIEMENS (SP):      R$ 15.340,50 ← Subtotal + DIFAL
ABB (RJ):          R$ 16.990,00 ← Subtotal + DIFAL
SCHNEIDER (MG):    R$ 15.204,50 ← Subtotal + DIFAL
```

#### Resumo DIFAL por Fornecedor
```
SIEMENS (SP):      R$ 104,50  (Operação Interestadual)
ABB (RJ):          R$ 110,00  (Operação Interestadual)
SCHNEIDER (MG):    R$ 104,50  (Operação Interestadual)
```

---

## Casos de Uso

### Caso 1: Fornecedor em SÃO PAULO (SP)
```
Alíquota SP: 18%
Alíquota AM: 18%
DIFAL = (18% - 7%) × R$ 950 = R$ 104,50
Total: R$ 950,00 + R$ 104,50 = R$ 1.054,50
Tipo: Operação Interestadual
```

### Caso 2: Fornecedor em GOIÁS (GO)
```
Alíquota GO: 15%
Alíquota AM: 18%
DIFAL = (18% - 7%) × R$ 500 = R$ 55,00
Total: R$ 500,00 + R$ 55,00 = R$ 555,00
Tipo: Operação Interestadual
```

### Caso 3: Fornecedor em MANAUS (AM)
```
Alíquota AM: 18%
Alíquota AM: 18%
DIFAL = 0 (mesma UF)
Total: R$ 950,00
Tipo: Operação Interna
```

---

## Impacto na Decisão de Compra

### Antes (sem DIFAL)
```
Fornecedor A (SP):    R$ 1.000,00  ← Aparenta mais barato
Fornecedor B (GO):    R$ 1.050,00
```

### Depois (com DIFAL)
```
Fornecedor A (SP):    R$ 1.110,00  ← Mais caro com DIFAL
Fornecedor B (GO):    R$ 1.105,00  ← Realmente melhor
```

O melhor preço pode mudar quando incluindo DIFAL!

---

## Aprovação Considerando DIFAL

### Botão: "💰 Melhor Preço"
Agora considera o **total incluindo DIFAL**:

```javascript
// Antes
Melhor = Menor(Preço Fornecedor A, Preço Fornecedor B, ...)

// Depois
Melhor = Menor(
  Preço A + DIFAL A,
  Preço B + DIFAL B,
  Preço C + DIFAL C,
  ...
)
```

---

## Alíquotas ICMS por Estado (2025)

| UF | ICMS | Tipo |
|---|---|---|
| AC | 17% | Acre |
| AL | 17% | Alagoas |
| AP | 18% | Amapá |
| **AM** | **18%** | **Amazonas (Destino)** |
| BA | 18% | Bahia |
| CE | 18% | Ceará |
| DF | 18% | Distrito Federal |
| ES | 18% | Espírito Santo |
| GO | 15% | Goiás |
| MA | 18% | Maranhão |
| MT | 15% | Mato Grosso |
| MS | 15% | Mato Grosso do Sul |
| MG | 18% | Minas Gerais |
| PA | 18% | Pará |
| PB | 18% | Paraíba |
| PR | 18% | Paraná |
| PE | 17% | Pernambuco |
| PI | 17% | Piauí |
| RJ | 18% | Rio de Janeiro |
| RN | 18% | Rio Grande do Norte |
| RS | 18% | Rio Grande do Sul |
| RO | 17.5% | Rondônia |
| RR | 18% | Roraima |
| SC | 18% | Santa Catarina |
| **SP** | **18%** | São Paulo |
| SE | 17% | Sergipe |
| TO | 15% | Tocantins |

---

## Fluxo de Uso

### 1. Cadastro de Fornecedor (Tab 2)
```
┌─────────────────────────────┐
│ Nome: SIEMENS              │
│ UF: [SP ▼]  ← Obrigatório  │
│ Cidade: São Paulo          │
│ CNPJ: 12.345.678/0001-90   │
└─────────────────────────────┘
```

### 2. Equalização (Tab 4)
```
Item: Cabo Elétrico (100 m @ R$ 9,50)

┌──────────────────────────────────────┐
│ SIEMENS (SP)                         │
├──────────────────────────────────────┤
│ Preço Unit: R$ 9,50                  │
│ Subtotal: R$ 950,00                  │
│ ICMS SP: 18%                         │
│ DIFAL: R$ 104,50                     │
│ Total: R$ 1.054,50 ✓ (verde)        │
└──────────────────────────────────────┘
```

### 3. Resumos Automáticos
```
💰 Resumo por Valor (com DIFAL):
SIEMENS: R$ 15.340,50 ✓

💰 DIFAL por Fornecedor:
SIEMENS (SP): R$ 1.456,50
```

### 4. Aprovação
```
[💰 Melhor Preço]
↓
✓ Aprovado: SIEMENS - R$ 15.340,50 (incluindo DIFAL)
```

---

## Considerações Importantes

### ⚠️ Quando Aplica DIFAL?
- ✅ Operações **interestaduais** (UF origem ≠ UF destino)
- ✅ Com **consumidor final** não-contribuinte
- ❌ Operações internas (mesma UF)
- ❌ Contribuintes do ICMS

### 📋 Documentação Necessária
- NF-e com indicação de DIFAL
- Comprovante de recolhimento
- GNRE (Guia Nacional de Recolhimento de Tributos)

### 🔍 Validação
- DIFAL deve ser recolhido ao estado de destino (AM)
- Prazo: até o 15º dia do mês seguinte
- Via GNRE ou através do ST (Substituto Tributário)

---

## Exemplos Práticos

### Exemplo 1: Comparação Simples
```
Item: Transformador 500KVA
Quantidade: 1
Base: R$ 4.200,00

FORNECEDOR A (SP):
├─ Preço: R$ 4.200,00
├─ DIFAL: (18% - 7%) × 4.200 = R$ 462,00
└─ Total: R$ 4.662,00

FORNECEDOR B (MG):
├─ Preço: R$ 4.100,00
├─ DIFAL: (18% - 7%) × 4.100 = R$ 451,00
└─ Total: R$ 4.551,00 ✓ Melhor

FORNECEDOR C (AM):
├─ Preço: R$ 4.150,00
├─ DIFAL: R$ 0,00 (mesmo estado)
└─ Total: R$ 4.150,00 ✓✓ Melhor!
```

### Exemplo 2: Múltiplos Itens
```
Cabo (100m × R$ 9,50):
├─ A (SP): R$ 950 + R$ 104,50 = R$ 1.054,50
├─ B (RJ): R$ 980 + R$ 107,80 = R$ 1.087,80

Disjuntor (2un × R$ 145):
├─ A (SP): R$ 290 + R$ 31,90 = R$ 321,90
├─ B (RJ): R$ 300 + R$ 33,00 = R$ 333,00

Subtotal:
├─ A (SP): R$ 1.375,40
├─ B (RJ): R$ 1.420,80
```

---

## FAQ

**P: O DIFAL é pago sempre?**
R: Apenas em operações interestaduais (UF origem ≠ AM). Operações internas não têm DIFAL.

**P: Quem recolhe o DIFAL?**
R: Geralmente a empresa compradora (Âmbar) na GNRE, ou o fornecedor (se ST).

**P: O valor do DIFAL entra no preço do produto?**
R: Sim, é um custo adicional ao preço base. Por isso entra na análise de melhor preço.

**P: Pode haver exceções?**
R: Sim, há casos especiais (Manaus Free Trade Zone, SUDAM, SUDENE, etc.). Nesses casos, use alíquotas específicas.

---

## Próximas Implementações (Opcionais)

- [ ] Modo manual de alíquotas (exceções especiais)
- [ ] ICMS ST (Substituição Tributária)
- [ ] PIS/COFINS na base de DIFAL
- [ ] Recolhimento por GNRE
- [ ] Relatório de DIFAL segregado
- [ ] Auditoria de DIFAL aplicado

---

**Status**: ✅ Implementado
**Data**: 25 de Maio de 2026
**Versão**: 1.0
**Próximo**: Testes e validação com dados reais

