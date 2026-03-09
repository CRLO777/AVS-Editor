# AVS Editor — Documentação Completa
**Versão:** 2.0 · **Formato:** Ferramenta offline (arquivo `.html` único)
**Compatibilidade:** GTA San Andreas · AVS / Model Extras (`.jsonc`)

---

## O que é o AVS Editor?

O **AVS Editor** é uma ferramenta visual de criação e edição de padrões de luz de emergência para veículos de GTA San Andreas. Ele substitui a edição manual de arquivos JSON/JSONC, oferecendo uma interface gráfica em tempo real onde é possível ver exatamente como os LEDs vão piscar, girar e sincronizar antes mesmo de colocar o arquivo no jogo.

A ferramenta funciona completamente offline — é um único arquivo `.html` que roda em qualquer navegador moderno, sem instalação, sem servidor, sem internet.

---

## Interface Geral

```
┌──────────────────────────────────────────────────────────────────────┐
│  HEADER: logo · abas de estado · ação · cores · refs · { }JSON       │
│          importar · exportar · idioma                                 │
├────────────┬────────────────────────────────────────┬────────────────┤
│  SIDEBAR   │  TOPBAR: ⊞ Grid / 💡 Light Display    │  PROPRIEDADES  │
│            │  LD TOOLBAR (só em Light Display)      │                │
│  Lista de  ├────────────────────────────────────────│  Painel de     │
│  materiais │  CENTRO (conteúdo do modo ativo)       │  edição do     │
│  ou luzes  │  Grid mode: grade animada + timeline   │  material      │
│            │  LD mode: canvas de posicionamento     │  selecionado   │
└────────────┴────────────────────────────────────────┴────────────────┘
```

### Header

- **Abas de estado** — cada aba é um grupo de sirenes. Clique para alternar, duplo clique para renomear, `×` para excluir
- **+ Estado** — adiciona estado vazio
- **⧉ Duplicar** — copia o estado ativo com todos os materiais
- **🎨 Cores** — abre o gerenciador de referências de cor
- **⚙️ Refs** — abre o gerenciador de referências de propriedade
- **{ } JSON** — abre o editor JSON completo (veja seção dedicada)
- **↑ Importar ▾** — menu: Importar `.json` ou `.jsonc`
- **↓ Exportar ▾** — menu: Exportar `.json` ou `.jsonc`
- **Seletor de idioma** — PT 🇧🇷 / EN 🇺🇸 / ES 🇪🇸 / RU 🇷🇺 / UK 🇺🇦

---

## Sistema de Estados

Um **estado** representa um modo de operação do veículo. Exemplos comuns:

| Estado | Uso típico |
|---|---|
| `1.Emergency` | Luzes de emergência ativas |
| `2.Park` | Modo estacionado, pisca lento |
| `3.Scene` | Iluminação de cena, LEDs fixos |

Cada estado tem seu próprio conjunto de materiais. O jogador alterna entre estados por teclas configuradas no mod.

**Operações:** adicionar · renomear (duplo clique) · duplicar · excluir (requer ao menos 1)

---

## Sistema de Materiais

Cada **material** é um slot de LED no modelo 3D, identificado por número (1–255) que deve coincidir com o nome do material/dummy no modelo.

### Sidebar (lista de materiais)

Cada item exibe: swatch de cor · ID editável · label (cor + referência + ↻ se rotator) · indicador de estado · 👁 ocultar · ✕ excluir.

**Editar ID:** clique no número, digite e confirme. O editor detecta conflitos e bloqueia IDs já existentes.

**Scroll do mouse** em qualquer campo numérico ajusta o valor. `Shift` = ±50, `Ctrl` = ±10, normal = ±1.

### Botões de rodapé
- **+ Material** — adiciona material com valores padrão
- **⧉** — duplica o material selecionado

---

## Modo Grid (Preview Clássico)

O modo padrão. Exibe quadrados numerados animados em tempo real.

- **Cor e brilho** — o quadrado acende com a cor e opacidade do material
- **Número + ms** — mostra ID e duração do segmento atual
- **Agulha giratória** — materiais Rotator exibem agulha animada com o ângulo atual
- **Clique** — seleciona o material para edição no painel de propriedades
- **ZOOM** — slider de 32px a 76px por célula
- **⏸ / ▶** — pausa ou retoma a animação

### Ocultar materiais no preview

O botão 👁 (aparece ao passar o mouse em cada item da sidebar) oculta o material do grid e timeline sem afetar o export.

- Material oculto: dimmed na sidebar com label riscado e badge `HIDDEN`
- Banner de aviso aparece no topo do grid informando quantos estão ocultos
- **👁 mostrar todos** — restaura tudo de uma vez (na sidebar e no banner)
- O arquivo exportado sempre contém todos os materiais, ocultos ou não

### Timeline

Cada material tem uma linha com blocos coloridos (ON) e escuros (OFF) proporcionais à duração em ms.

- Clique num bloco para editar o segmento nas propriedades
- **+** ao final de cada linha adiciona novo segmento
- Materiais Rotator exibem barra especial com direção e velocidade
- Materiais ocultos ficam com opacidade reduzida na timeline
- **MS padrão** — duração usada ao adicionar segmentos com o botão `+`

---

## Modo Light Display (💡)

O modo Light Display permite sobrepor pontos de luz animados sobre uma imagem do veículo, simulando visualmente como os LEDs ficarão no modelo 3D.

### Ativando

Clique em **💡 Light Display** na topbar. A sidebar muda para lista de luzes, a timeline é ocultada e o canvas ocupa todo o espaço central.

### Importando a imagem

Clique em **📁 Imagem** na toolbar. Aceita qualquer formato de imagem (PNG, JPG, etc.). A imagem é centralizada e dimensionada automaticamente ao ser carregada.

### Controles de imagem

**📐 Ajustar** — ativa o modo de edição de imagem (botão fica laranja, cursor muda para ✥):
- **Arrastar** — move a imagem livremente pelo canvas
- **Scroll do mouse** — zoom centrado no cursor (0.05× até 10×)

**⊡ Fit** — reencaixa e centraliza a imagem no tamanho ideal automaticamente.

> Os controles de scroll/mover funcionam em qualquer modo — você não precisa ativar 📐 para usar o scroll. O modo 📐 é necessário apenas para arrastar a imagem.

### Adicionando luzes

1. Selecione o material no dropdown **Mat:** da toolbar
2. Escolha a forma: **○ Corona**, **▬ Rect** ou **▲ Tri**
3. Clique na imagem para posicionar a luz — ela fica vinculada ao material selecionado
4. Ajuste **Escala** (slider) e **Rot** (campo numérico em graus) com a luz selecionada

### Movendo luzes

Arraste qualquer luz posicionada para reposicioná-la. As coordenadas são armazenadas em posição normalizada relativa à imagem (0..1), portanto ao mover/escalar a imagem as luzes acompanham automaticamente.

### Comportamento da animação

- **LED ON** → luz acende com cor completa + glow radial correspondente ao material
- **LED OFF** → luz fica quase invisível (18% de opacidade)
- A luz selecionada exibe um anel tracejado ao redor

### Formas disponíveis

| Forma | Descrição |
|---|---|
| ○ Corona | Glow circular radial com núcleo brilhante — ideal para LEDs individuais |
| ▬ Rect | Barra retangular com glow elíptico — ideal para lightbars |
| ▲ Tri | Triângulo com glow — ideal para sinalizações direcionais |

### Sidebar no modo LD

Exibe lista de todas as luzes posicionadas com: swatch de cor · ID do material · ✕ excluir. Clicar numa luz a seleciona.

### Operações de luz

- **⧉** (toolbar) — duplica a luz selecionada (deslocada levemente)
- **✕** (toolbar ou sidebar) — apaga a luz selecionada
- Luzes do mesmo material piscam sincronizadas — útil para simular múltiplos LEDs no mesmo dummy

> **Esta função não afeta o export.** As luzes do Light Display são exclusivamente visuais e nunca entram no arquivo `.json` ou `.jsonc` gerado.

---

## Painel de Propriedades

Exibe e edita todos os parâmetros do material selecionado. Todas as alterações refletem imediatamente no preview.

### Cor
Dropdown com as cores das referências. O link **✏️ editar cores** abre o modal de referências de cor.

### Estado Inicial
Toggle ON / OFF — define se o LED começa aceso ou apagado ao iniciar o ciclo.

### Size / Inertia — dois modos

**Manual** — campos `Size` (tamanho do corona/LED) e `Inertia` (suavidade de transição, opcional).

**Referência** — vincula a uma referência de propriedade nomeada. Todos os materiais usando a mesma referência se atualizam ao editar a referência.

### Shadow (Sombra)
Checkbox para ativar. Campos: **Offset** · **Size** · **Texture** (nome da textura, ex.: `comet`).

### Rotator
Checkbox para ativar rotação. Quando ativo:
- **Direção** — `clockwise` · `counter-clockwise` · `switch`
- **Speed (ms)** — tempo para completar um ciclo
- **Radius (°)** — ângulo percorrido (360 = rotação completa, 90 = varredura de 90°)
- **Offset (°)** — ângulo inicial
- **Type** — tipo de interpolação (`linear`)

> Materiais com Rotator **não possuem Pattern** — o campo Speed substitui os segmentos de piscar.

### Pattern (Padrão de piscar)

Lista de segmentos alternados ON/OFF. O estado do primeiro segmento é determinado pelo **Estado Inicial**.

Exemplo: estado inicial OFF, pattern `[300, 300]` → apagado 300ms, aceso 300ms, repete.

Pattern complexo: estado OFF, `[50, 50, 50, 50, 50, 300]` → cinco pulsos rápidos seguidos de pausa longa.

Pattern `[]` (vazio) = LED estático no estado inicial.

**Operações:** editar duração de cada segmento · ✕ excluir segmento · + adicionar · Limpar todos.

### JSON deste material
Caixa no rodapé do painel com o JSON do material atual, pronto para copiar. Atualiza automaticamente.

---

## Editor JSON Completo ({ } JSON)

Acessado pelo botão **{ } JSON** no header. Abre um modal com o JSON completo do projeto para visualização e edição direta.

### Modos

**Sirens** — exibe apenas o bloco `{references, states}`, idêntico ao arquivo `.json` exportado.

**Full .jsonc** — exibe o arquivo completo com `metadata`, `lights`, `carcols` e demais blocos. Se o projeto foi importado de um `.jsonc`, todos os blocos originais são preservados.

### Funcionalidades

- **Edição direta** — o textarea é editável. Qualquer JSON válido pode ser digitado ou colado
- **Validação em tempo real** — ao digitar, a barra inferior mostra `✓ JSON válido` ou a mensagem de erro exata com a posição do problema
- **Borda vermelha** no textarea indica JSON inválido
- **Sincronização automática** — enquanto o modal está aberto, qualquer mudança feita nos painéis do editor (pattern, cor, rotator etc.) atualiza o JSON em tempo real
- **⌥ Formatar** — indenta e formata automaticamente (útil após colar JSON compacto)
- **↺ Recarregar** — descarta edições e volta ao estado atual do editor
- **✓ Aplicar** — faz parse do JSON, valida a estrutura e carrega no editor. No modo Full `.jsonc`, extrai o bloco `sirens` e atualiza o contexto para exportação futura

---

## Referências de Cor (🎨)

Paleta de cores nomeadas compartilhada por todos os materiais.

Cada cor tem: **Nome** · **R, G, B, A** (0–255) · **Picker rápido** (aplica RGB sem alterar Alpha).

**Edição dos valores numéricos:** use teclado ou setas do campo. Scroll do mouse está desativado neste painel para evitar desseleção acidental.

- Valores são clampeados automaticamente entre 0 e 255
- Campos vazios são preenchidos com 0 ao sair do campo

**Por que usar referências?** Alterar a tonalidade de `red` uma vez atualiza todos os materiais que usam essa cor.

---

## Referências de Propriedade (⚙️)

Grupos de propriedades nomeados e reutilizáveis.

Exemplo de referência `strobe`: `{"size": 0.4, "inertia": 0.5}`

Exemplo de referência `rotator`: `{"size": 0.2, "state": 1, "type": "rotator", "rotator": {"direction": "clockwise", "type": "linear", "time": 500}}`

**Operações:** adicionar referência · adicionar/renomear/excluir campos individuais (as chaves são editáveis).

---

## Import e Export

### Exportar .json
Gera `{references, states}` — o formato puro de sirenes.

### Exportar .jsonc
Gera o arquivo completo no formato Model Extras:
- Se importado de `.jsonc`: reconstrói o arquivo original com o bloco `sirens` atualizado, preservando `metadata`, `lights`, `carcols` etc.
- Se criado do zero: gera `.jsonc` mínimo com cabeçalho `metadata` básico.

### Importar .json
Carrega um arquivo `{references, states}`.

### Importar .jsonc
Lê arquivo `.jsonc` do Model Extras com suporte a:
- Comentários `//` em qualquer posição
- Trailing commas
- Extração automática do bloco `sirens`, preservando o restante para reexport
- **Cor inline** — `"color": {"red":255,...}` é automaticamente convertida para referência nomeada
- **Direction numérico** — `0/1/2` normalizados para `clockwise/counter-clockwise/switch`
- **Campo `time`** mapeado automaticamente para `speed`

---

## Sincronização de Materiais

Materiais com o mesmo `patternTotal` (soma de todos os ms do pattern) são **automaticamente sincronizados** — quando qualquer um completa um ciclo, todos os outros com o mesmo total reiniciam juntos.

Para criar alternância (vermelho e azul), configure dois materiais com o mesmo pattern total e estados iniciais opostos (um ON, um OFF).

---

## Formato JSON de Saída

```json
{
    "references": {
        "colors": {
            "red":    {"red": 255, "green": 20,  "blue": 20,  "alpha": 150},
            "blue":   {"red": 51,  "green": 102, "blue": 255, "alpha": 150},
            "white":  {"red": 255, "green": 255, "blue": 255, "alpha": 128},
            "orange": {"red": 255, "green": 98,  "blue": 0,   "alpha": 128}
        },
        "strobe": {"size": 0.4, "inertia": 0.5}
    },
    "states": {
        "1.Emergency": {
            "1": {"color": "red",   "state": 0, "pattern": [300, 300], "size": 0.4},
            "2": {"color": "red",   "state": 1, "pattern": [300, 300], "size": 0.4},
            "3": {"color": "white", "state": 1, "reference": "strobe",
                  "rotator": {"direction": "clockwise", "type": "linear",
                               "speed": 1000, "radius": 360, "offset": 0}}
        }
    }
}
```

### Tabela de campos

| Campo | Tipo | Descrição |
|---|---|---|
| `color` | string | Nome de uma referência de cor |
| `state` | 0 ou 1 | Estado inicial: 0=OFF, 1=ON |
| `pattern` | array de números | Durações em ms, alternando ON/OFF. Vazio = estático |
| `size` | número | Tamanho do corona/LED |
| `inertia` | número | Suavidade de transição (opcional) |
| `reference` | string | Referência de propriedade (substitui size/inertia) |
| `shadow.offset` | número | Deslocamento da sombra |
| `shadow.size` | número | Tamanho da sombra |
| `shadow.type` | string | Nome da textura (ex.: `"comet"`) |
| `rotator.direction` | string | `"clockwise"` · `"counter-clockwise"` · `"switch"` |
| `rotator.speed` | número | Ms por ciclo |
| `rotator.radius` | número | Graus percorridos por ciclo |
| `rotator.offset` | número | Ângulo inicial em graus |
| `rotator.type` | string | `"linear"` |

> Materiais com `rotator` **não exportam** o campo `pattern`.

---

## Idiomas Suportados

| | Código | Idioma |
|---|---|---|
| 🇧🇷 | PT | Português (padrão) |
| 🇺🇸 | EN | English |
| 🇪🇸 | ES | Español |
| 🇷🇺 | RU | Русский |
| 🇺🇦 | UK | Українська |

---

## Dicas de Uso

**Alternância vermelho/azul clássica:**
Crie materiais 1 e 3 (red, state 0) e materiais 2 e 4 (blue, state 1), todos com pattern `[300, 300]`. Todos sincronizam e alternam em perfeita oposição.

**Padrão wig-wag:**
Pattern `[50, 50, 50, 50, 50, 300]` — cinco pulsos rápidos, pausa longa, repete.

**LED estático (cena):**
Pattern `[]` + Estado inicial 1 = sempre aceso.

**Rotator de varredura (não 360°):**
Direction `switch`, radius `90`, offset `-45` — agulha varre de -45° a +45° e volta.

**Focar num grupo de materiais:**
Oculte os outros com 👁. O preview mostra só o que importa, sem afetar o export.

**Simular múltiplos LEDs no mesmo material (Light Display):**
Adicione várias luzes vinculadas ao mesmo material. Todas piscam em sincronia, simulando vários LEDs controlados pelo mesmo dummy — exatamente como funciona no jogo.

**Verificar o JSON antes de exportar:**
Abra **{ } JSON** e alterne para **Full .jsonc** para ver o arquivo completo como ficará após o export. Edite diretamente se necessário e clique em **✓ Aplicar**.

**Importar .jsonc de veículo existente:**
Importe o arquivo direto. Edite apenas o bloco `sirens`. Exporte como `.jsonc` — o arquivo reconstruído preserva `carcols`, `lights` e demais blocos intactos.

**Scroll do mouse para ajuste fino:**
Em qualquer campo numérico do editor (exceto os campos RGB das cores), role o mouse para ajustar. `Shift` = ±50, `Ctrl` = ±10.

---

## Requisitos Técnicos

- Qualquer navegador moderno: Chrome, Firefox, Edge, Opera
- Sem instalação, sem internet, sem dependências externas
- Arquivo único `.html` — abra diretamente de qualquer pasta

---

*Desenvolvido como ferramenta de apoio para modders de GTA San Andreas.*
