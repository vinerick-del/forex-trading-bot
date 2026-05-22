# 🚀 Guia Rápido - Sistema Âmbar ENERGIA

## Pré-requisitos
- Navegador moderno (Chrome, Firefox, Edge, Safari)
- Arquivo: `teste_app.html`

## Fluxo Completo em 5 Minutos

### 1️⃣ CRIAR UM NOVO PROCESSO (Tab: ➕ Novo Processo)
```
Preencha os campos:
├─ Número DATAGED: DG-2025-001
├─ Descrição: Cabos Elétricos Q1 2025
├─ Centro de Custo: CC-001
├─ Responsável: João Silva
└─ Tipo: Cabos Elétricos

Clique em "Criar Processo"
➜ Redirecionará para Cotação
```

### 2️⃣ BUSCAR MATERIAIS NO SAP (Tab: 🔌 SAP Fiori)
```
Opção A - Por Código:
├─ Digite: 100101
└─ Clique em "🔍 Buscar no SAP"

Opção B - Por Descrição:
├─ Digite: Cabo
└─ Clique em "🔍 Buscar no SAP"

Resultado:
└─ Clique em "Importar" em cada material

Veja "Itens Importados Recentemente" atualizar ✅
```

### 3️⃣ CONFIGURAR COTAÇÃO (Tab: ✏️ Cotação)
```
1. Selecione o processo criado
2. Adicione 2-3 fornecedores:
   ├─ Nome: Siemens
   ├─ UF: SP
   └─ Prazo: 15 dias
   
3. Para cada item importado, preencha:
   ├─ Quantidade
   └─ Preço unitário
   
4. Preencha preços por fornecedor na tabela
5. Clique em "💾 Salvar Cotação"
```

### 4️⃣ REGISTRAR FICHAS TÉCNICAS (Tab: 📎 Fichas Técnicas)
```
1. Selecione o processo
2. Para cada item:
   ├─ Clique em "Adicionar"
   ├─ Preencha:
   │  ├─ Número da Ficha: FT-2025-001
   │  ├─ Fabricante: Siemens
   │  ├─ Aprovador: Maria Silva
   │  ├─ Data: Data de hoje
   │  └─ Checklist: Marque tudo
   └─ Clique "Registrar Ficha"
   
✅ Status muda de "⏳ Pendente" para "✓ Assinado"
```

### 5️⃣ VER ANÁLISE E RECOMENDAÇÃO (Tab: ⭐ Análise & Recomendação)
```
1. Selecione o processo
2. Veja:
   ├─ ✓ Recomendação (melhor fornecedor)
   ├─ 📊 Gráfico de comparativo
   ├─ ⭐ Rating de fornecedores (com estrelas)
   └─ 📈 Histórico de preços

Automático: O sistema recomenda o melhor preço
```

### 6️⃣ APROVAR PROCESSO (Tab: ✓ Aprovação)
```
1. Selecione o processo
2. Veja resumo:
   ├─ Total Orçado
   ├─ Economia
   └─ Status Técnico (✅ Todas aprovadas)
   
3. Preencha dados de aprovação:
   ├─ Nome: Seu nome
   ├─ Data: Automática
   └─ Observações: Opcional
   
4. ASSINATURA DIGITAL:
   ├─ Desenhe assinatura no canvas
   ├─ Ou clique "Limpar" para refazer
   └─ Hash gera automaticamente
   
5. Clique "✓ Aprovar Processo"
➜ Status muda para APROVADO ✅
```

### 7️⃣ GERAR RELATÓRIO (Tab: 📄 Relatórios)
```
1. Selecione o processo aprovado
2. Veja preview do relatório
3. Opções:
   ├─ "📄 Exportar PDF Completo" → Salva PDF
   └─ "🖨️ Imprimir" → Abre print do navegador
```

### 8️⃣ CONSULTAR HISTÓRICO (Tab: 📜 Histórico)
```
Filtros disponíveis:
├─ Status: Rascunho / Aprovado
├─ Tipo: Cabos / Transformadores / Disjuntores
└─ Período: 7 / 30 / 90 dias

Resultado:
├─ Lista todos processos com:
│  ├─ Data de criação
│  ├─ Tipo de material
│  ├─ Quantidade de itens
│  └─ Fichas técnicas completas
└─ Pode combinar múltiplos filtros
```

## 📊 DASHBOARD (Tab: 📊 Dashboard)
```
Mostra em tempo real:
├─ KPIs: Ativos, Fichas Pendentes, Taxa Aprovação, Tempo Médio
├─ Top 5 Fornecedores (com contagem)
├─ Economia por Categoria
├─ Alertas (fichas pendentes)
└─ Timeline (processos em andamento)

Atualiza automaticamente ao criar/aprovar processos
```

## 🔔 NOTIFICAÇÕES
```
Canto superior direito:
├─ Clique no sino 🔔 para ver notificações
├─ Mostra até 10 últimas ações
└─ Verde (✓) = Sucesso
   Vermelho (✕) = Erro
   Azul (ℹ️) = Info
```

## 💾 DADOS
```
Tudo salva automaticamente em localStorage:
├─ Processos: localStorage['processos_amazon']
└─ Histórico preços: localStorage['preco_historico']

Para limpar tudo:
├─ Abra DevTools (F12)
├─ Console
├─ localStorage.clear()
└─ Recarregue
```

## ⚡ DICAS IMPORTANTES

1. **Crie vários fornecedores** para ver a comparação funcionar
2. **Sempre marque o checklist** ao registrar ficha técnica
3. **Preços por fornecedor** na tabela de cotação
4. **Desenhe assinatura** com o mouse no canvas
5. **Salve a cotação** antes de ir para próxima aba
6. **Use notificações** para rastrear o que aconteceu

## 🐛 Se Algo Não Funcionar

### Canvas de Assinatura não desenha
```
✅ Use mouse (não touchpad)
✅ Clique em "Limpar" e tente novamente
✅ Certifique-se que Canvas está visível
```

### Dados desaparecem
```
✅ Verifique se localStorage está habilitado
✅ Verifique limite de quota do navegador
✅ Limpe cache (Ctrl+Shift+Del)
```

### Gráfico não aparece
```
✅ Selecione um processo com fornecedores
✅ Adicione preços para todos os itens
✅ Reabra a aba de Análise
```

### PDF não exporta
```
✅ Certifique-se que RelatorioProcessoSelect tem um valor
✅ Use Chrome/Firefox (Edge e Safari podem ter restrições)
✅ Verifique console (F12) para erros
```

## 📈 EXEMPLO COMPLETO (Copy-Paste)

```javascript
// No DevTools Console, para popular dados de teste:
state.processos = [{
  dataged: 'TEST-2025-001',
  descricao: 'Teste Automático',
  centroCusto: 'CC-001',
  responsavel: 'Admin',
  tipo: 'cabos',
  dataCriacao: new Date().toISOString().split('T')[0],
  status: 'RASCUNHO',
  fornecedores: [
    {nome: 'Fornecedor A', uf: 'SP', prazo: 15},
    {nome: 'Fornecedor B', uf: 'RJ', prazo: 20}
  ],
  itens: [{
    cod: '100101',
    desc: 'Cabo Teste',
    und: 'm',
    qtd: 100,
    precoUnitario: 10,
    precos: [9.50, 11.00],
    fichas_tecnicas: []
  }],
  fichas_tecnicas: [],
  assinaturas: {}
}];

localStorage.setItem('processos_amazon', JSON.stringify(state.processos));
location.reload();
```

## ✅ CHECKLIST DE TESTE COMPLETO

- [ ] Criar novo processo
- [ ] Buscar itens no SAP
- [ ] Importar materiais
- [ ] Adicionar 2+ fornecedores
- [ ] Preencher preços
- [ ] Salvar cotação
- [ ] Registrar ficha técnica
- [ ] Marcar conformidade
- [ ] Ver recomendação
- [ ] Ver gráfico de comparativo
- [ ] Desenhar assinatura
- [ ] Aprovar processo
- [ ] Exportar PDF
- [ ] Ver histórico com filtros
- [ ] Consultar dashboard
- [ ] Verificar notificações

---

**Tempo estimado**: 5-10 minutos  
**Navegador**: Qualquer um moderno  
**Requerimentos**: Nenhum (100% client-side)  
**Persistência**: localStorage  

🎉 **Pronto para usar!**
