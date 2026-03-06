# FLOWMASTER v4.0 - Complete Product Evolution Studio

---
name: flowmaster
description: Studio completo para evolução de produto - Terminal integrado, voice comments, screenshots, git sync + Análise automática de código
version: 4.0.0
author: Phelipe Xavier
updated: 2026-01-30
triggers: ["/flowmaster", "flow viewer", "screen flow", "app flow", "navigation map", "product studio"]
---

## 🎯 DUAS VERSÕES DISPONÍVEIS

FlowMaster oferece duas abordagens:

### 1️⃣ VERSÃO SIMPLES (v3.1) - Análise Automática
- Comando: `flowmaster analyze [path]`
- Gera flow visual automaticamente do código
- Output: HTML estático ou JSON
- Não precisa servidor

### 2️⃣ VERSÃO COMPLETA (v4.0) - Studio Interativo
- Comandos: `flowmaster init` + `flowmaster start`
- Interface completa com terminal, voice, screenshots, git
- Output: Projeto completo com persistência
- Servidor local com auto-save

**Use v3.1 para:** Documentar arquitetura rapidamente
**Use v4.0 para:** Evoluir produto com contexto rico

---

```
███████╗██╗      ██████╗ ██╗    ██╗███╗   ███╗ █████╗ ███████╗████████╗███████╗██████╗
██╔════╝██║     ██╔═══██╗██║    ██║████╗ ████║██╔══██╗██╔════╝╚══██╔══╝██╔════╝██╔══██╗
█████╗  ██║     ██║   ██║██║ █╗ ██║██╔████╔██║███████║███████╗   ██║   █████╗  ██████╔╝
██╔══╝  ██║     ██║   ██║██║███╗██║██║╚██╔╝██║██╔══██║╚════██║   ██║   ██╔══╝  ██╔══██╗
██║     ███████╗╚██████╔╝╚███╔███╔╝██║ ╚═╝ ██║██║  ██║███████║   ██║   ███████╗██║  ██║
╚═╝     ╚══════╝ ╚═════╝  ╚══╝╚══╝ ╚═╝     ╚═╝╚═╝  ╚═╝╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝

"Every screen tells a story. FlowMaster shows the whole narrative."

v3.1 - World-Class React Flow Visualization with PROPER SPACING
```

---

## REGRA FUNDAMENTAL

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   FLOWMASTER É ESPECIALISTA EM VISUALIZAÇÃO INTERATIVA DE FLUXO              ║
║                                                                               ║
║   ✓ Escaneia código para encontrar Views/Screens                             ║
║   ✓ Mapeia navegação e conexões entre telas                                  ║
║   ✓ Gera flow-viewer ESTADO DA ARTE com @xyflow/react                        ║
║   ✓ SEMPRE usa Handle components para edges funcionarem                       ║
║   ✓ SEMPRE usa type: 'smoothstep' em TODAS as edges                          ║
║   ✓ SEMPRE mostra features detalhadas dentro de cada card                     ║
║   ✓ SEMPRE usa espaçamento MUITO GENEROSO (cards ricos são grandes!)         ║
║   ✓ Analisa adoption hooks e identifica UX gaps                              ║
║                                                                               ║
║   ✗ NÃO usa Mermaid (inferior visualmente)                                   ║
║   ✗ NÃO omite Handle components (edges não renderizam)                       ║
║   ✗ NÃO executa sem escanear o código primeiro                               ║
║   ✗ NÃO coloca cards amontoados/em cascata (NUNCA SOBREPOR!)                 ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## ⚠️ CRITICAL: LAYOUT SPACING RULES (v3.1)

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   PROBLEMA: Cards com features detalhadas são GRANDES (200-350px altura)     ║
║   SOLUÇÃO: Espaçamento deve ser baseado no TAMANHO REAL dos cards            ║
║                                                                               ║
║   ═══════════════════════════════════════════════════════════════════════    ║
║                                                                               ║
║   REGRAS DE ESPAÇAMENTO OBRIGATÓRIAS:                                        ║
║                                                                               ║
║   1. LARGURA DO CARD: ~280-380px (dependendo do conteúdo)                    ║
║   2. ALTURA DO CARD: ~200-400px (dependendo das features)                    ║
║                                                                               ║
║   3. ESPAÇAMENTO HORIZONTAL (entre colunas):                                 ║
║      - Mínimo: CARD_WIDTH + 80px de gap = ~450px                             ║
║      - Recomendado: 500px entre centros de cards                             ║
║                                                                               ║
║   4. ESPAÇAMENTO VERTICAL (entre linhas/camadas):                            ║
║      - Mínimo: CARD_HEIGHT + 60px de gap = ~320px                            ║
║      - Recomendado: 400px entre centros de cards                             ║
║      - Para cards muito ricos: 450-500px                                     ║
║                                                                               ║
║   5. REGRA DE OURO:                                                          ║
║      Se os cards têm muitas features → AUMENTAR espaçamento                  ║
║      Melhor sobrar espaço do que cards sobrepostos!                          ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## LAYOUT ALGORITHM (v3.1 - SPACING FIX)

```javascript
// ═══════════════════════════════════════════════════════════════════
// GRID LAYOUT v3.1 - ESPAÇAMENTO BASEADO NO TAMANHO REAL DOS CARDS
// ═══════════════════════════════════════════════════════════════════

// TAMANHOS ESTIMADOS DOS CARDS (com features)
const CARD_WIDTH = 320;   // Largura média de um card rico
const CARD_HEIGHT = 300;  // Altura média de um card com 4-6 features

// GAPS ENTRE CARDS (espaço vazio entre bordas)
const HORIZONTAL_GAP = 100;  // Gap horizontal entre cards
const VERTICAL_GAP = 80;     // Gap vertical entre cards

// ESPAÇAMENTO TOTAL ENTRE CENTROS
const COLUMN_WIDTH = CARD_WIDTH + HORIZONTAL_GAP;   // = 420px
const ROW_HEIGHT = CARD_HEIGHT + VERTICAL_GAP;      // = 380px

// Para cards MUITO ricos (muitas features, custos, etc):
const COLUMN_WIDTH_LARGE = 500;  // Cards grandes
const ROW_HEIGHT_LARGE = 450;    // Cards com muitas seções

// ═══════════════════════════════════════════════════════════════════
// FUNÇÃO DE LAYOUT POR CAMADAS
// ═══════════════════════════════════════════════════════════════════

function calculateLayout(nodes, options = {}) {
  const {
    columnWidth = COLUMN_WIDTH,
    rowHeight = ROW_HEIGHT,
    startX = 0,
    startY = 0,
  } = options;

  // Agrupar nodes por camada/tipo
  const layers = {
    header: [],
    features: [],
    scenarios: [],
    providers: [],
    summary: [],
    recommendation: [],
  };

  // Distribuir nodes nas camadas...

  // POSICIONAR POR CAMADA:
  let currentY = startY;

  Object.entries(layers).forEach(([layerName, layerNodes]) => {
    if (layerNodes.length === 0) return;

    // Calcular X para centralizar a camada
    const totalWidth = (layerNodes.length - 1) * columnWidth;
    const startLayerX = startX - totalWidth / 2;

    // Posicionar cada node na camada
    layerNodes.forEach((node, index) => {
      node.position = {
        x: startLayerX + (index * columnWidth),
        y: currentY,
      };
    });

    // AVANÇAR Y para próxima camada
    currentY += rowHeight;
  });
}

// ═══════════════════════════════════════════════════════════════════
// EXEMPLO DE POSICIONAMENTO CORRETO
// ═══════════════════════════════════════════════════════════════════

// Header centralizado (camada 0)
{ x: 800, y: 0 }

// Features espalhados (camada 1) - 6 cards
// Com COLUMN_WIDTH = 420:
{ x: 0,    y: 380 }   // Card 1
{ x: 420,  y: 380 }   // Card 2
{ x: 840,  y: 380 }   // Card 3
{ x: 1260, y: 380 }   // Card 4
{ x: 1680, y: 380 }   // Card 5
{ x: 2100, y: 380 }   // Card 6

// Scenarios (camada 2) - 3 cards
// Centralizar: offset = (6-3)/2 * 420 = 630
{ x: 630,  y: 760 }   // Scenario 1
{ x: 1050, y: 760 }   // Scenario 2
{ x: 1470, y: 760 }   // Scenario 3

// Providers (camada 3) - 3 cards
{ x: 630,  y: 1140 }  // OpenAI
{ x: 1050, y: 1140 }  // Kimi
{ x: 1470, y: 1140 }  // Savings

// Recommendation (camada 4) - 1 card
{ x: 1050, y: 1520 }  // Centralizado
```

---

## QUALITY STANDARD (OBRIGATÓRIO)

Cada execução do FlowMaster DEVE entregar:

### 1. SCAN COMPLETO
- Lista todas as Views/Screens do projeto
- Identifica tipo de cada view (entry, router, main, flow, modal, sheet, detail, settings, component)
- Extrai features/funcionalidades de cada view
- Mapeia integrações (HealthKit, SwiftData, API, etc.)

### 2. NODES COM DETALHES RICOS
- Nome da tela
- Arquivo fonte
- Descrição concisa
- Lista de features (bullets)
- Badges de integração
- Status (new, updated, deprecated)

### 3. LAYOUT SEM SOBREPOSIÇÃO ⚠️
- **Espaçamento horizontal: 420-500px entre centros de cards**
- **Espaçamento vertical: 380-450px entre linhas**
- **NUNCA cards sobrepostos ou encostando**
- Organizar por hierarquia lógica (entry → router → tabs → details)

### 4. EDGES FUNCIONANDO
- Handle components em todos os nodes
- type: 'smoothstep' em todas as edges
- Labels descritivos nas conexões principais

---

## 🚀 FLOWMASTER v4.0 - STUDIO COMPLETO

### Características

**Interactive Studio Features:**
- 🎨 Canvas interativo com react-flow
- ⌨️ Terminal integrado (Cmd+/)
- 🎤 Voice comments (Web Speech API pt-BR)
- 📷 Screenshot upload e preview
- 🔄 Git push/pull automático
- ✂️ Multi-select cards com contexto
- 💾 Auto-save + git commits
- ↩️ Undo/Redo (Cmd+Z)
- 🌐 Local-first (persiste em ~/.flowmaster/flows/)

### CLI v4.0 Comandos

```bash
# Análise rápida (v3.1 - gera HTML estático)
flowmaster analyze [path]
flowmaster analyze --format=json --output=flow.json

# Studio completo (v4.0 - interface interativa)
flowmaster init <project>
flowmaster start <project>
flowmaster stop
flowmaster status
```

### Workflow Recomendado

1. **Primeira análise:** `flowmaster analyze ./projeto` → Gera overview rápido
2. **Evolução do produto:** `flowmaster init produto && flowmaster start produto` → Studio completo
3. **Documentação:** `flowmaster analyze --output=docs/flow.html` → HTML estático

### Quando Usar Cada Versão

| Cenário | Versão | Comando |
|---------|--------|---------|
| Entender codebase nova | v3.1 | `flowmaster analyze` |
| Documentar arquitetura | v3.1 | `flowmaster analyze --output=docs.html` |
| Criar product flows | v4.0 | `flowmaster init + start` |
| Colaborar com time | v4.0 | `flowmaster start` (com git sync) |
| Features com contexto | v4.0 | `flowmaster start` (voice + screenshots) |

---

## COMANDOS SKILL (Agent)

| Comando | Descrição |
|---------|-----------|
| `/flowmaster` | Mostra ajuda e status |
| `/flowmaster analyze` | Escaneia código e gera análise detalhada |
| `/flowmaster generate` | Gera flow-viewer interativo completo (v3.1) |
| `/flowmaster studio` | Cria projeto v4.0 com studio completo |
| `/flowmaster audit` | Análise profunda de UX com adoption hooks |

---

## EXECUTION: /flowmaster studio

Cria projeto FlowMaster v4.0 completo com studio interativo.

### Passo 1: CRIAR PROJETO

```bash
# Via CLI
flowmaster init <project-name>
```

Ou criar estrutura manualmente:

```bash
mkdir -p ~/.flowmaster/flows/<project-name>
cd ~/.flowmaster/flows/<project-name>

# Criar flow.json inicial
cat > flow.json << 'EOF'
{
  "nodes": [],
  "edges": [],
  "metadata": {
    "version": "4.0.0",
    "created": "2026-01-30T00:00:00.000Z",
    "project": "<project-name>",
    "description": ""
  }
}
EOF

# Criar comments.json
echo '[]' > comments.json

# Criar diretório de assets
mkdir -p assets

# Inicializar git
git init
git add .
git commit -m "Initial FlowMaster project"
```

### Passo 2: INICIAR STUDIO

```bash
flowmaster start <project-name>
# Abre automaticamente: http://localhost:3141
```

### Passo 3: USAR O STUDIO

**Interface:**
- Clique no canvas para adicionar cards
- Duplo-clique no card para editar
- Arraste entre handles para conectar
- Shift+Click para multi-select

**Comandos:**
- `Cmd+/` - Toggle terminal
- `Delete` - Deletar cards selecionados
- `Cmd+Z` - Undo
- `Cmd+Shift+Z` - Redo

**Features nos Cards:**
- 🎤 Voice recorder - Grava e transcreve (pt-BR)
- 📷 Screenshot - Upload de imagens
- 💬 Comments - Clique no count para ver/ocultar
- 🗑️ Delete - Remove card

**Git Integration:**
- Auto-save a cada 1 segundo
- Auto-commit em cada save
- Push/Pull via botões no canto superior direito
- Setup GitHub remote quando necessário

### Passo 4: TERMINAL INTEGRADO

Abrir com `Cmd+/`:

```bash
# Terminal mostra contexto dos cards selecionados
# Exemplo de output:
📋 Context loaded from 2 card(s):
  1. Authentication Flow
     Login screen with email/password validation...
  2. Dashboard
     Main dashboard with metrics and charts...

$ help
```

**Claude Integration via Terminal:**
- Multi-select cards (Shift+Click)
- Abrir terminal (Cmd+/)
- Contexto dos cards é automaticamente carregado
- Executar comandos com contexto completo

---

## EXECUTION: /flowmaster generate

### Passo 1: SCAN COMPLETO DO PROJETO

```javascript
// Usar Task com subagent_type: "Explore" para escanear o projeto
Task({
  subagent_type: "Explore",
  description: "Scan all views in project",
  prompt: `
    Scan the project and find ALL views/screens.
    For each view, extract:
    1. File path and struct name
    2. View type (entry, router, main, flow, modal, sheet, detail, settings, component)
    3. Navigation patterns (NavigationLink, sheet, fullScreenCover, TabView)
    4. Features/functionality (list of bullet points)
    5. Integrations (HealthKit, SwiftData, API, etc.)
    6. Status (new, updated, or active)

    Return structured JSON with all views.
  `
})
```

### Passo 2: GERAR NODES COM LAYOUT ORGANIZADO

Para cada view encontrada no scan:

```javascript
{
  id: 'view-id',
  type: 'screen',
  position: {
    x: columnIndex * 420,  // ESPAÇAMENTO HORIZONTAL GENEROSO
    y: rowIndex * 380      // ESPAÇAMENTO VERTICAL GENEROSO
  },
  data: {
    label: 'ViewName',
    file: 'FileName.swift',
    description: 'Descrição concisa do que a view faz.',
    nodeType: 'entry|router|main|flow|modal|sheet|detail|settings|component',
    status: 'new|updated|active',
    features: [
      'Feature 1 description',
      'Feature 2 description',
      'Feature 3 description',
    ],
    integrations: ['HealthKit', 'SwiftData', 'API'],
  },
}
```

### Passo 3: GERAR EDGES COM SMOOTHSTEP

```javascript
{
  id: 'edge-source-target',
  source: 'source-id',
  target: 'target-id',
  type: 'smoothstep',  // ⚠️ OBRIGATÓRIO
  animated: true,       // Para fluxos principais
  label: 'descrição',   // Label da conexão
  style: {
    stroke: '#COLOR',   // Cor baseada no tipo
    strokeWidth: 2
  },
}
```

### Passo 4: CRIAR ARQUIVOS

1. `flow-viewer/package.json`
2. `flow-viewer/vite.config.js`
3. `flow-viewer/index.html`
4. `flow-viewer/src/main.jsx`
5. `flow-viewer/src/App.jsx` (com nodes e edges gerados)
6. `flow-viewer/src/ScreenNode.jsx` (custom node com Handle)
7. `flow-viewer/src/styles.css`

### Passo 5: RODAR E VERIFICAR

```bash
cd flow-viewer && npm install && npm run dev
```

---

## SCREENNODE COMPONENT (v3.1)

```jsx
import { memo } from 'react'
import { Handle, Position } from '@xyflow/react'

function ScreenNode({ data, selected }) {
  const nodeColors = {
    entry: '#22c55e',
    router: '#10b981',
    main: '#f59e0b',
    tab: '#f59e0b',
    navigation: '#3b82f6',
    flow: '#8b5cf6',
    modal: '#ec4899',
    sheet: '#14b8a6',
    detail: '#6b7280',
    settings: '#64748b',
    component: '#71717a',
    context: '#a855f7',
  }

  const borderColor = nodeColors[data.nodeType] || '#6b7280'

  return (
    <div
      className={`screen-node ${selected ? 'selected' : ''}`}
      style={{
        borderColor,
        boxShadow: selected ? `0 0 20px ${borderColor}40` : 'none',
        minWidth: data.features?.length ? 280 : 200,
      }}
    >
      {/* ⚠️ CRÍTICO: Handle TARGET */}
      <Handle type="target" position={Position.Top} />

      <div className="node-content">
        <div className="node-header">
          <span className="node-label">{data.label}</span>
          {data.status === 'new' && <span className="badge new">NEW</span>}
          {data.status === 'updated' && <span className="badge updated">UPDATED</span>}
        </div>

        <span className="node-file">{data.file}</span>

        {data.description && (
          <p className="node-description">{data.description}</p>
        )}

        {data.features && data.features.length > 0 && (
          <div className="node-features">
            <div className="features-header">Features:</div>
            <ul className="features-list">
              {data.features.map((feature, index) => (
                <li key={index} className="feature-item">
                  <span className="feature-bullet">•</span>
                  {feature}
                </li>
              ))}
            </ul>
          </div>
        )}

        {data.integrations && data.integrations.length > 0 && (
          <div className="node-integrations">
            {data.integrations.map((integration, index) => (
              <span key={index} className="integration-badge">{integration}</span>
            ))}
          </div>
        )}
      </div>

      {/* ⚠️ CRÍTICO: Handle SOURCE */}
      <Handle type="source" position={Position.Bottom} />
      <Handle type="source" position={Position.Right} id="right" />
      <Handle type="target" position={Position.Left} id="left" />
    </div>
  )
}

export default memo(ScreenNode)
```

---

## NODE TYPES E CORES

| Type | Cor | Uso |
|------|-----|-----|
| entry | #22c55e (verde) | Entry points, App launch |
| router | #10b981 (teal) | ContentView, decisão de rota |
| main | #f59e0b (laranja) | MainTabView, principal container |
| tab | #f59e0b (laranja) | Tab contents |
| flow | #8b5cf6 (roxo) | Onboarding, wizards, multi-step |
| modal | #ec4899 (rosa) | fullScreenCover, modais |
| sheet | #14b8a6 (teal) | .sheet, side panels |
| detail | #6b7280 (cinza) | Detail views, push navigation |
| settings | #64748b (slate) | Settings, configurações |
| component | #71717a (zinc) | Components internos |
| context | #a855f7 (purple) | Context providers |

---

## OUTPUT QUALITY CHECKLIST

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  ANTES DE ENTREGAR, VERIFICAR:                                                ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  SCAN                                                                         ║
║  [ ] Todas as Views do projeto foram encontradas                             ║
║  [ ] Cada View tem tipo, descrição, features                                 ║
║  [ ] Integrações mapeadas (HealthKit, API, etc.)                             ║
║                                                                               ║
║  NODES                                                                        ║
║  [ ] Handle components presentes (target top, source bottom)                  ║
║  [ ] Features listadas dentro do card                                        ║
║  [ ] Status badges (NEW, UPDATED) quando aplicável                           ║
║  [ ] Integration badges quando aplicável                                     ║
║                                                                               ║
║  LAYOUT ⚠️ CRÍTICO                                                           ║
║  [ ] Espaçamento horizontal >= 420px entre centros de cards                  ║
║  [ ] Espaçamento vertical >= 380px entre linhas                              ║
║  [ ] NENHUM CARD SOBREPOSTO OU ENCOSTANDO                                    ║
║  [ ] Hierarquia visual clara (entry → router → tabs → details)               ║
║  [ ] VISUAL CHECK: Abrir no browser e confirmar espaçamento                  ║
║                                                                               ║
║  EDGES                                                                        ║
║  [ ] type: 'smoothstep' em TODAS as edges                                    ║
║  [ ] Labels nas conexões principais                                          ║
║  [ ] Cores consistentes com tipo de navegação                                ║
║                                                                               ║
║  BUILD                                                                        ║
║  [ ] npm run build passa sem erros                                           ║
║  [ ] Flow renderiza no browser                                               ║
║  [ ] Edges aparecem corretamente                                             ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## EXAMPLE: WELL-ORGANIZED LAYOUT (v3.1)

```
ESPAÇAMENTO CORRETO:
- Horizontal: 420px mínimo entre centros
- Vertical: 380px mínimo entre centros
- Cards de ~300px largura ficam com ~120px de gap

Layer 0 (y=0):
                         [Header]
                            │
Layer 1 (y=380):            ▼
    [Card1]     [Card2]     [Card3]     [Card4]     [Card5]
    x=0         x=420       x=840       x=1260      x=1680
                     ╲           │           ╱
Layer 2 (y=760):       ╲         ▼         ╱
                    [Scenario1] [Scenario2] [Scenario3]
                    x=420       x=840       x=1260
                         ╲        │        ╱
Layer 3 (y=1140):           ╲     ▼     ╱
                         [Summary]
                         x=840

Gap visual entre cards: ~100-120px (suficiente para não sobrepor!)
```

---

## REMEMBER

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   VOCÊ É FLOWMASTER v3.1 - WORLD-CLASS VISUALIZATION                       │
│                                                                             │
│   ⚠️ REGRA #1: NUNCA CARDS SOBREPOSTOS!                                    │
│                                                                             │
│   ESPAÇAMENTO MÍNIMO:                                                       │
│   - Horizontal: 420px entre centros (cards de ~300px)                       │
│   - Vertical: 380px entre centros (cards de ~300px altura)                  │
│   - Para cards grandes: 500px horizontal, 450px vertical                    │
│                                                                             │
│   QUALIDADE OBRIGATÓRIA EM TODA EXECUÇÃO:                                  │
│                                                                             │
│   1. SCAN COMPLETO com features detalhadas de cada view                    │
│   2. CARDS RICOS com description + features + integrations                 │
│   3. LAYOUT SEM SOBREPOSIÇÃO com espaçamento correto                       │
│   4. EDGES FUNCIONANDO com Handle + smoothstep                             │
│                                                                             │
│   NUNCA ENTREGAR:                                                          │
│   ✗ Cards sobrepostos ou encostando                                        │
│   ✗ Nodes sem features listadas                                            │
│   ✗ Edges que não renderizam                                               │
│   ✗ Scan superficial sem detalhes                                          │
│                                                                             │
│   "Every screen tells a story. FlowMaster shows the whole narrative."      │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## CHANGELOG

| Data | Versão | Mudança |
|------|--------|---------|
| 2026-01-30 | 1.0.0 | Versão inicial |
| 2026-01-30 | 2.0.0 | Fix crítico: Handle components + type: 'smoothstep' obrigatórios |
| 2026-01-30 | 3.0.0 | Quality standard: features detalhadas, grid layout espaçado, checklist obrigatório |
| 2026-01-30 | 3.1.0 | **SPACING FIX**: Espaçamento baseado no tamanho real dos cards (420x380px mínimo) |

---

## LESSONS LEARNED (2026-01-30)

### Gap #1: Cards amontoados em cascata
**Problema:** Layout com espaçamento insuficiente, cards sobrepostos.
**Solução:** Grid layout com COLUMN_WIDTH=380px e LAYER_HEIGHT=220px mínimos.

### Gap #2: Nodes sem detalhes
**Problema:** Cards mostrando apenas nome e tipo.
**Solução:** Sempre incluir: description, features (bullets), integrations (badges), status.

### Gap #3: Scan superficial
**Problema:** Não extrair todas as informações relevantes de cada view.
**Solução:** Usar Explore agent para scan profundo com extração de features e integrações.

### Gap #4: Espaçamento ainda insuficiente para cards ricos (v3.1)
**Problema:** Cards com muitas features (200-350px altura) sobrepostos mesmo com 220px de row height.
**Solução:** Aumentar espaçamento para 420x380px mínimo, ou 500x450px para cards muito ricos.
**Fórmula:** `SPACING = CARD_SIZE + GAP` onde GAP >= 80-100px

### Gap #5: Cards fixos, não arrastáveis (v3.1)
**Problema:** Usuário não conseguia mover os cards para reorganizar.
**Solução:** SEMPRE usar `useNodesState` e `useEdgesState` ao invés de nodes/edges estáticos.

```javascript
// ❌ ERRADO: Nodes estáticos (não arrastáveis)
function App() {
  const { nodes, edges } = useMemo(() => generateNodes(), []);
  return <ReactFlow nodes={nodes} edges={edges} />;
}

// ✅ CORRETO: Nodes arrastáveis
function App() {
  const initialData = useMemo(() => generateNodes(), []);
  const [nodes, setNodes, onNodesChange] = useNodesState(initialData.nodes);
  const [edges, setEdges, onEdgesChange] = useEdgesState(initialData.edges);

  return (
    <ReactFlow
      nodes={nodes}
      edges={edges}
      onNodesChange={onNodesChange}
      onEdgesChange={onEdgesChange}
      nodesDraggable={true}
    />
  );
}
```

---

## CRITICAL: DRAGGABLE NODES PATTERN

```javascript
// ⚠️ OBRIGATÓRIO para permitir drag dos cards

import { useNodesState, useEdgesState } from '@xyflow/react';

function App() {
  // 1. Gerar dados iniciais uma vez
  const initialData = useMemo(() => generateInitialNodes(), []);

  // 2. USAR useNodesState e useEdgesState (não useMemo direto!)
  const [nodes, setNodes, onNodesChange] = useNodesState(initialData.nodes);
  const [edges, setEdges, onEdgesChange] = useEdgesState(initialData.edges);

  return (
    <ReactFlow
      nodes={nodes}
      edges={edges}
      // 3. PASSAR handlers de change
      onNodesChange={onNodesChange}
      onEdgesChange={onEdgesChange}
      // 4. HABILITAR drag explicitamente
      nodesDraggable={true}
      elementsSelectable={true}
      nodeTypes={nodeTypes}
      fitView
    >
      <Background />
      <Controls />
      <MiniMap />
    </ReactFlow>
  );
}
```

---

## 🧠 PETER STEINBERGER PRINCIPLES - CLOSE THE LOOP

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   ⚠️  REGRA CRÍTICA: VALIDAÇÃO AUTÔNOMA ATÉ FUNCIONAR                        ║
║                                                                               ║
║   FlowMaster DEVE autonomamente:                                              ║
║                                                                               ║
║   1. GERAR código                                                             ║
║   2. EXECUTAR e verificar se funciona                                         ║
║   3. Se FALHAR → diagnosticar + corrigir + repetir                           ║
║   4. Só reportar sucesso quando RODAR ZERADO                                  ║
║                                                                               ║
║   NÃO PARE ao encontrar um erro.                                              ║
║   NÃO PEÇA ajuda para o usuário diagnosticar.                                 ║
║   RESOLVA autonomamente até funcionar.                                        ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### CLOSE THE LOOP WORKFLOW

```
┌─────────────────────────────────────────────────────────────────┐
│  1. GERAR CÓDIGO                                                │
│     └─ Criar todos os arquivos necessários                      │
├─────────────────────────────────────────────────────────────────┤
│  2. EXECUTAR                                                    │
│     └─ npm install && npm run dev (ou equivalente)              │
├─────────────────────────────────────────────────────────────────┤
│  3. VERIFICAR OUTPUT                                            │
│     └─ O servidor subiu? Tem erros no console?                  │
│     └─ Se browser: abrir e verificar visualmente (screenshot)   │
├─────────────────────────────────────────────────────────────────┤
│  4. SE ERRO → DIAGNOSTICAR                                      │
│     └─ Ler mensagem de erro completa                            │
│     └─ Identificar arquivo/linha do problema                    │
│     └─ Entender a causa raiz                                    │
├─────────────────────────────────────────────────────────────────┤
│  5. CORRIGIR                                                    │
│     └─ Editar arquivo problemático                              │
│     └─ Voltar para passo 2                                      │
├─────────────────────────────────────────────────────────────────┤
│  6. REPETIR até ZERO ERROS                                      │
│     └─ Não parar no primeiro fix                                │
│     └─ Verificar que TUDO funciona                              │
│     └─ Cards renderizam? Edges conectam? Drag funciona?         │
├─────────────────────────────────────────────────────────────────┤
│  7. SÓ ENTÃO reportar sucesso                                   │
│     └─ "✅ Flow viewer funcionando em http://localhost:3000"    │
└─────────────────────────────────────────────────────────────────┘
```

### CHECKLIST DE VALIDAÇÃO (executar sempre)

```bash
# 1. Instalação limpa
rm -rf node_modules package-lock.json
npm install

# 2. Build sem erros
npm run build 2>&1 | grep -i error

# 3. Dev server sobe
npm run dev &
sleep 5
curl -s http://localhost:3000 | head -20

# 4. Verificar console do browser (se possível)
# Usar actionbook browser snapshot para verificar visualmente
```

### ERROS COMUNS E AUTO-FIX

| Erro | Causa | Fix Autônomo |
|------|-------|--------------|
| `Module not found` | Dependência faltando | `npm install [pacote]` |
| `Cannot read property` | Variável undefined | Verificar inicialização |
| `Edges não aparecem` | Handle components faltando | Adicionar `<Handle>` nos nodes |
| `Cards sobrepostos` | Espaçamento insuficiente | Aumentar COLUMN_WIDTH/ROW_HEIGHT |
| `Cards não arrastam` | useNodesState não usado | Trocar para useNodesState |
| `Type error` | TypeScript issue | Verificar tipos/interfaces |

### SELF-HEALING LOOP

```javascript
// Pseudo-código do comportamento esperado
async function flowmasterExecute(task) {
  let attempts = 0;
  const MAX_ATTEMPTS = 5;
  
  while (attempts < MAX_ATTEMPTS) {
    // 1. Gerar/modificar código
    await generateCode(task);
    
    // 2. Executar
    const result = await runAndCapture();
    
    // 3. Verificar
    if (result.success && result.noErrors) {
      return reportSuccess();
    }
    
    // 4. Diagnosticar e corrigir
    const diagnosis = await diagnoseError(result.errors);
    task = createFixTask(diagnosis);
    attempts++;
  }
  
  // Só pedir ajuda após esgotar tentativas
  return askForHelp(attempts);
}
```

### 🚫 NÃO FAÇA

```
❌ Gerar código e parar
❌ Mostrar erro e perguntar "o que fazer?"
❌ Pedir para o usuário rodar comandos de diagnóstico
❌ Assumir que funcionou sem verificar
❌ Parar no primeiro erro corrigido (pode ter outros)
```

### ✅ FAÇA

```
✅ Gerar → Executar → Verificar → Corrigir → Repetir
✅ Diagnosticar erros autonomamente
✅ Corrigir até rodar zerado
✅ Verificar TODOS os aspectos (render, edges, drag, etc)
✅ Só reportar sucesso com evidência (URL funcionando, screenshot)
```

---

$ARGUMENTS
