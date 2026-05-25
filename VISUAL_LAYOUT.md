# 📐 Estrutura Visual da Nova Interface

## 🎨 Layout Geral

```
┌────────────────────────────────────────────────────────────────────────────┐
│ ⚡ Âmbar                      Dashboard                    👤 Admin        │ ← Top Header
├─────────────┬──────────────────────────────────────────────────────────────┤
│             │                                                              │
│  📊 Dash    │  📊 Dashboard Executivo                                      │
│  📋 Process │                                                              │
│  🏢 Supp    │  ┌─────────────┬──────────────┬──────────────┬────────────┐ │
│  💰 Quote   │  │ Processos   │ Fornecedores │ Cotações em  │ Cotações   │ │
│  ⚖️ Equali  │  │ Ativos:     │ Cadastrados: │ Aberto:      │ Pendentes: │ │
│  📈 Report  │  │ 12          │ 28           │ 5            │ 3          │ │
│  ⚙️ Config  │  └─────────────┴──────────────┴──────────────┴────────────┘ │
│             │                                                              │
│             │  ┌─────────────────────────────────────────────────────────┐│
│ MENU        │  │  📋 ÚLTIMOS PROCESSOS                      [Ver Mais]  ││
│ PRINCIPAL   │  ├─────────────────────────────────────────────────────────┤│
│             │  │ DATAGED    │ Descrição      │ Status │ Fornecedores   ││
│ ANÁLISE     │  ├─────────────┼────────────────┼────────┼────────────────┤│
│             │  │ DG-2025-001 │ Cabos de Força │ Ativo  │ 3              ││
│ CONFIGURAÇÃO│  │ DG-2025-002 │ Equipamentos   │ Pend.  │ 5              ││
│             │  │ DG-2025-003 │ Transformador  │ Ativo  │ 2              ││
│             │  └─────────────┴────────────────┴────────┴────────────────┘│
│             │                                                              │
└─────────────┴──────────────────────────────────────────────────────────────┘

← Sidebar (260px) → ← Main Content Area (Responsivo) →
```

## 📋 Página de Processos

```
┌────────────────────────────────────────────────────────────────┐
│  📋 Gerenciar Processos                                        │
│  Crie e acompanhe processos de compra                          │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │ Novo Processo                                            │ │
│  ├──────────────────────────────────────────────────────────┤ │
│  │ Número DATAGED *                Descrição *             │ │
│  │ [DG-2025-XXX...........]  [Descrição do processo.......]│ │
│  │                                                          │ │
│  │ Centro de Custo              Responsável              │ │
│  │ [CC-001...........]           [Nome responsável.....]   │ │
│  │                                                          │ │
│  │ [✓ Criar Processo]  [Cancelar]                         │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │  📋 PROCESSOS CADASTRADOS                [Ver Mais]    │ │
│  ├──────────────────────────────────────────────────────────┤ │
│  │ DATAGED │ Descrição │ Responsável │ Fornec. │ Status   │ │
│  ├─────────┼───────────┼─────────────┼─────────┼──────────┤ │
│  │ DG-01   │ Cabos     │ João Silva  │ 3       │ ✓ Ativo  │ │
│  │ DG-02   │ Equipam.  │ Maria Costa │ 5       │ ⚠ Pend.  │ │
│  │ DG-03   │ Transform │ Pedro Lima  │ 2       │ ✓ Ativo  │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

## 🏢 Página de Fornecedores

```
┌────────────────────────────────────────────────────────────────┐
│  🏢 Cadastro de Fornecedores                                   │
│  Gerencie todos os seus fornecedores                           │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │ Novo Fornecedor                                          │ │
│  ├──────────────────────────────────────────────────────────┤ │
│  │ Nome da Empresa *              CNPJ *                   │ │
│  │ [Nome completo............]  [00.000.000/0000-00......]│ │
│  │                                                          │ │
│  │ Email *                        Telefone                │ │
│  │ [email@fornecedor.com......]  [(11) 9999-9999.......]  │ │
│  │                                                          │ │
│  │ Estado (UF) *                  Cidade                  │ │
│  │ [-- Selecione --]              [Cidade......]          │ │
│  │                                                          │ │
│  │ [✓ Cadastrar]  [Cancelar]                              │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │  📋 FORNECEDORES CADASTRADOS                           │ │
│  ├──────────────────────────────────────────────────────────┤ │
│  │ Empresa │ CNPJ │ Email │ UF │ Status │ Ações         │ │
│  ├─────────┼──────┼───────┼────┼────────┼───────────────┤ │
│  │ SIEMENS │ 12.. │ siemens@.. │ SP │ ✓ │ [✎] [✕]     │ │
│  │ ABB     │ 98.. │ abb@....   │ MG │ ✓ │ [✎] [✕]     │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

## 💰 Página de Cotações

```
┌────────────────────────────────────────────────────────────────┐
│  💰 Cotações e Equalizacão                                     │
│  Gerencie cotações de fornecedores                             │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ℹ️ Selecione um Processo                                     │
│     Escolha um processo de compra para começar a gerenciar     │
│     cotações                                                   │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │ Selecionar Processo                                      │ │
│  ├──────────────────────────────────────────────────────────┤ │
│  │ Processo DATAGED                                         │ │
│  │ [-- Selecione um processo --                           ▼] │
│  │   - DG-2025-001 - Cabos de Força                         │ │
│  │   - DG-2025-002 - Equipamentos Elétricos                 │ │
│  │   - DG-2025-003 - Transformadores                        │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

## ⚖️ Página de Equalizacão

```
┌────────────────────────────────────────────────────────────────┐
│  ⚖️ Análise Comparativa                                        │
│  Compare propostas de fornecedores                             │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ✓ Funcionalidade Pronta                                      │
│    Sistema de equalizacão com cálculo de DIFAL, comparativo    │
│    de preços e recomendação inteligente integrado.             │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐ │
│  │ ⚙️ Configurar Fornecedores                              │ │
│  ├──────────────────────────────────────────────────────────┤ │
│  │ Processo DATAGED *                                       │ │
│  │ [-- Selecione --                                       ▼] │
│  │                                                          │ │
│  │ [+ Adicionar Item]  [+ Adicionar Fornecedor]            │ │
│  └──────────────────────────────────────────────────────────┘ │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

## 🎨 Componentes Principais

### KPI Cards
```
┌─────────────────────────────────────┐
│ ▮ (Cor indicativa)                  │
│                                     │
│  Processos Ativos          📋       │
│  12                                 │
│                                     │
└─────────────────────────────────────┘
```

### Buttons
```
[✓ Ação Principal]  [◯ Ação Secundária]  [✓ Sucesso]  [✕ Deletar]
     (Azul)             (Cinza)          (Verde)      (Vermelho)
```

### Badges
```
✓ Ativo    ⚠ Pendente    ✗ Crítico    ◯ Neutro
(Verde)    (Amarelo)     (Vermelho)   (Cinza)
```

### Form Inputs
```
Label
[_________________________________]  ← Foco: border azul, shadow
```

### Alerts
```
┌─────────────────────────────────────┐
│ ℹ️  Título da Mensagem              │
│    Descrição detalhada da mensagem   │
└─────────────────────────────────────┘
 ▮ (Cor: Azul/Verde/Amarelo/Vermelho)
```

## 📐 Dimensões e Espaçamento

```
Sidebar:           260px (Desktop), 180px (Tablet), 150px (Mobile)
Top Header:        64px height
Content Padding:   2rem (Desktop), 1rem (Mobile)
Card Padding:      1.5rem
Gap entre Cards:   1.5rem
Button Padding:    0.5rem 1rem
Input Padding:     0.5rem 0.75rem
Border Radius:     6-10px (Cards), 12px (Badges)
```

## 🎨 Cores em Uso

```
Backgrounds:
- Page:    #f3f4f6 (Gray-100)
- Cards:   #ffffff (White)
- Hover:   #f9fafb (Gray-50)

Text:
- Primary:    #111827 (Gray-900)
- Secondary:  #4b5563 (Gray-600)
- Muted:      #9ca3af (Gray-400)

Buttons:
- Primary:    #3b82f6 (Blue)
- Success:    #10b981 (Green)
- Warning:    #d97706 (Orange)
- Danger:     #dc2626 (Red)

Borders:
- Default:    #e5e7eb (Gray-200)
```

## 📱 Responsividade

```
Desktop (1024px+)
├─ Sidebar: 260px
├─ Grid: 4 colunas
└─ Layout: Full

Tablet (768-1024px)
├─ Sidebar: 200px
├─ Grid: 2 colunas
└─ Layout: Adjusted

Mobile (480-768px)
├─ Sidebar: 180px
├─ Grid: 1 coluna
└─ Forms: Full-width

Extra Small (<480px)
├─ Sidebar: 150px
├─ Buttons: Full-width
└─ Layout: Minimal
```

---

**Status**: ✅ Layout profissional pronto para uso

