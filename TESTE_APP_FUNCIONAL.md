# 🧪 Guia de Testes - app_funcional.html

**Data**: 25 de Maio de 2026  
**Arquivo**: `app_funcional.html`  
**Status**: ✅ **PRONTO PARA TESTE**

---

## 📋 O Que Testamos

- ✅ Estado e persistência de dados (localStorage)
- ✅ Cálculo DIFAL para 27 UFs brasileiras
- ✅ Estrutura HTML com todos os elementos necessários
- ✅ Funções JavaScript para CRUD de fornecedores e processos
- ✅ Sistema de equalizacao com comparativo de preços

---

## 🚀 Como Abrir e Testar

### Opção 1: Arquivo Local
```bash
# Abra direto no navegador
file:///home/user/forex-trading-bot/app_funcional.html
```

### Opção 2: Com Servidor HTTP
```bash
cd /home/user/forex-trading-bot
python3 -m http.server 8000
# Acesse: http://localhost:8000/app_funcional.html
```

---

## ✅ Checklist de Testes

### 1. Dashboard (Página Inicial)
- [ ] Página carrega com 4 KPI cards
- [ ] KPI cards mostram: Processos (0), Fornecedores (0), Cotações (0), Economia (0%)
- [ ] Tabela de últimos processos está vazia ou mostra últimas entradas

### 2. Cadastro de Fornecedores
```
Passos:
1. Clique "🏢 Fornecedores" no sidebar
2. Preencha o formulário:
   - Nome: SIEMENS BRASIL
   - Email: vendas@siemens.com.br
   - Telefone: (11) 3333-4444
   - CNPJ: 12.345.678/0001-90
   - UF: SP (dropdown)
   - Cidade: São Paulo
3. Clique "✓ Cadastrar Fornecedor"
```

**Esperado:**
- [ ] Mensagem de sucesso apareça
- [ ] Fornecedor apareça na tabela abaixo
- [ ] KPI de Fornecedores atualize para "1"
- [ ] Dados persistam após refresh (F5)

### 3. Cadastro de Processos
```
Passos:
1. Clique "📋 Processos" no sidebar
2. Preencha o formulário:
   - DATAGED: DG-2025-001
   - Descrição: Cabos de Força
   - Centro de Custo: CC-001
   - Responsável: João Silva
3. Clique "✓ Criar Processo"
```

**Esperado:**
- [ ] Processo apareça na tabela
- [ ] KPI de Processos atualize para "1"
- [ ] Dropdown em "⚖️ Equalizacao" liste o novo processo

### 4. Workflow de Equalizacao (COMPLETO)
```
Passos:
1. Clique "⚖️ Equalizacao"
2. Selecione "DG-2025-001" no dropdown
3. Clique "+ Adicionar Item"
4. Preencha dados do item:
   - Tipo Material: Cabo
   - Código: CBN-001
   - Descrição: Cabo de Cobre 10mm²
   - Quantidade: 100
5. Clique "+ Adicionar Fornecedor"
6. Configure fornecedor (deve aparecer dropdown)
7. Selecione "SIEMENS BRASIL"
8. Preencha preço unitário: 50,00
```

**Esperado (TESTE CRÍTICO):**
- [ ] Tabela comparativa apareça com item
- [ ] Coluna do fornecedor mostre preço
- [ ] Cálculo de DIFAL seja aplicado (SP -> AM)
- [ ] Total com DIFAL apareça na tabela
- [ ] Resumo por Fornecedor mostre valor total
- [ ] Resumo por Material mostre melhor preço
- [ ] Recomendação indique SIEMENS como melhor

### 5. Teste DIFAL (Cálculo Crítico)
```
Dados de Entrada:
- Fornecedor SP (São Paulo)
- Preço Unitário: 1000,00
- Quantidade: 1
```

**Esperado:**
- ICMS SP: 18%
- ICMS AM: 18%
- DIFAL: (18 - 7) × 1000 / 100 = 110,00
- Total com DIFAL: 1110,00

### 6. Múltiplos Fornecedores
```
Passos:
1. Crie mais um fornecedor (ex: ABB, UF=MG)
2. Em Equalizacao, clique "+ Adicionar Fornecedor"
3. Selecione ABB
4. Preencha preço menor (ex: 45,00)
```

**Esperado:**
- [ ] Tabela mostre 2 colunas de fornecedores
- [ ] ABB seja destacado em verde (melhor preço)
- [ ] DIFAL calculado corretamente para MG
- [ ] Resumo atualizado com ambos fornecedores

### 7. Adicionar Item Adicional
```
Em Equalizacao, clique "+ Adicionar Item" novamente
```

**Esperado:**
- [ ] Novo item apareça na tabela
- [ ] Ambos fornecedores tenham preço vazio
- [ ] Resumos se mantenham apenas com itens preenchidos

### 8. Persistência de Dados
```
Passos:
1. Preencha vários formulários
2. Pressione F5 (refresh)
3. Navegue entre páginas
```

**Esperado:**
- [ ] Todos os dados persistam após refresh
- [ ] localStorage contenha: fornecedores_ambar e processos_amazon
- [ ] KPIs mantenham valores corretos

### 9. Responsividade
```
Testes:
- Desktop (1920x1080)
- Tablet (768x1024)
- Mobile (375x667)
```

**Esperado:**
- [ ] Layout adapte-se a cada tamanho
- [ ] Sidebar se mantenha acessível
- [ ] Tabelas fiquem scrolláveis em mobile
- [ ] Botões ficarem ao menos 44px de altura

### 10. Notificações e Feedback
```
Ações que devem gerar notificação:
- Cadastrar fornecedor
- Criar processo
- Adicionar item
- Adicionar fornecedor/proposta
```

**Esperado:**
- [ ] Notificação apareça no topo
- [ ] Desapareça após 4 segundos
- [ ] Mensagem seja clara e útil

---

## 🐛 Testes de Edge Cases

### 1. Campos Vazios
```
Tentar criar processo sem DATAGED
```
**Esperado:** Alert: "Preencha DATAGED e Descrição (*)"

### 2. Fornecedor Duplicado
```
Tentar cadastrar fornecedor com mesmo nome
```
**Esperado:** Alert: "Fornecedor já cadastrado"

### 3. Processo Sem Fornecedor
```
Criar processo e item sem selecionar fornecedor em equalizacao
```
**Esperado:** Item visível mas não apareça em resumos

### 4. Deletar Proposta
```
Com 2+ fornecedores, clicar ✕ em um
```
**Esperado:** 
- [ ] Proposta removida
- [ ] Coluna desapareça
- [ ] Resumos atualizem

---

## 📊 Testes de Dados

### Dados de Teste Sugeridos

**Fornecedores:**
```
1. SIEMENS BRASIL (SP)
2. ABB (MG) 
3. WEG (SC)
4. SCHNEIDER (RJ)
```

**Processos:**
```
1. DG-2025-001 - Cabos de Força
2. DG-2025-002 - Transformadores
3. DG-2025-003 - Disjuntores
```

**Itens:**
```
Item 1: CBN-001 - Cabo 10mm² (100 un)
Item 2: TRF-001 - Transformador 100kVA (5 un)
Item 3: DSJ-001 - Disjuntor Bipolar 40A (50 un)
```

---

## 🔍 Verificação de Console (F12)

Abra DevTools (F12) e verifique:

```javascript
// Verificar state
console.log(state);

// Verificar localStorage
console.log(JSON.parse(localStorage.getItem('fornecedores_ambar')));
console.log(JSON.parse(localStorage.getItem('processos_amazon')));

// Testar DIFAL
console.log(calcularDIFAL('SP', 1000));
console.log(calcularDIFAL('MG', 1000));
console.log(calcularDIFAL('AM', 1000));
```

**Esperado:**
- Nenhum erro em vermelho (red errors)
- Warnings sobre console são OK
- State mostra estrutura correta

---

## ✨ Teste Visual

### Elementos Esperados

**Sidebar:**
- [ ] Logo com ⚡ Âmbar
- [ ] 7 menu items: Dashboard, Processos, Fornecedores, Cotações, Equalizacao, Relatórios, Configurações
- [ ] Item ativo destacado em azul

**Header Superior:**
- [ ] Nome da página atual
- [ ] Ícone de usuário (👤 Admin)

**Cores:**
- [ ] Fundo: Cinza claro (#f3f4f6)
- [ ] Sidebar: Cinza escuro/Preto
- [ ] Primário: Azul (#1e40af, #3b82f6)
- [ ] Sucesso: Verde (#10b981)
- [ ] Danger: Vermelho (#dc2626)

---

## 📝 Relatório de Teste

Após testar tudo acima, preencha:

```
TESTE REALIZADO POR: _______________
DATA: _______________
NAVEGADOR: _______________
SISTEMA OPERACIONAL: _______________

✅ TESTES PASSADOS: ___ / 10
⚠️  TESTES COM AVISO: ___
❌ TESTES FALHADOS: ___

PROBLEMAS ENCONTRADOS:
[Liste aqui qualquer problema encontrado]

FUNCIONALIDADES TESTADAS COM SUCESSO:
- [x] Lorem ipsum
- [x] Lorem ipsum
```

---

## 🎯 Resultado Esperado Final

```
✅ Dashboard carrega com dados corretos
✅ Fornecedores podem ser cadastrados e aparecem em lista
✅ Processos podem ser criados
✅ Equalizacao funciona com múltiplos fornecedores
✅ DIFAL é calculado corretamente
✅ Dados persistem após refresh
✅ Interface é responsiva
✅ Notificações funcionam
✅ Nenhum erro de JavaScript no console
✅ App está pronto para produção
```

---

## 🚀 Próximos Passos

Se todos os testes passarem:

1. ✅ App pronto para uso
2. ✅ Dados são persistidos
3. ✅ Funcionalidades integradas
4. ✅ Design profissional

Se encontrar problemas:

1. 📝 Anote o problema
2. 🔍 Verifique o console (F12)
3. 📧 Reporte o problema

---

**Status**: 🎉 **APP PRONTO PARA TESTES FUNCIONAIS**

