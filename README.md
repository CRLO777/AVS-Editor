<img width="1365" height="634" alt="image" src="https://github.com/user-attachments/assets/66950720-0d16-4c69-98ac-4bc9cd4ec983" />
# AVS Editor — Documentação Completa

**Versão:** Final · **Formato:** Ferramenta offline (arquivo `.html` único)
**Compatibilidade:** GTA San Andreas · AVS / Model Extras (`.jsonc`)

---

## O que é o AVS Editor?

O **AVS Editor** é uma ferramenta visual de criação e edição de padrões de luz de emergência para veículos de GTA San Andreas. Ele substitui a edição manual de arquivos JSON/JSONC, oferecendo uma interface gráfica em tempo real onde é possível ver exatamente como os LEDs vão piscar, girar e sincronizar antes mesmo de colocar o arquivo no jogo.

A ferramenta funciona completamente offline — é um único arquivo `.html` que roda em qualquer navegador moderno, sem instalação, sem servidor, sem internet.

---

## Para quem é esta ferramenta?

- Modders de GTA San Andreas que trabalham com mods de luz de emergência (AVS, Model Extras)
- Criadores de veículos que precisam configurar padrões de sirene complexos
- Qualquer pessoa que edite arquivos `.json` ou `.jsonc` de sirenes manualmente e queira uma alternativa visual

---

## Interface

A interface é dividida em quatro áreas principais:

```
┌──────────────────────────────────────────────────────────────────┐
│  HEADER: logo · abas de estado · botões de ação · idioma        │
├────────────┬─────────────────────────────────┬───────────────────┤
│  SIDEBAR   │  PREVIEW GRID (topo)            │  PROPRIEDADES     │
│  Lista de  │  Grade animada em tempo real    │  Painel de        │
│  materiais │─────────────────────────────────│  edição do        │
│            │  TIMELINE (baixo)               │  material         │
│            │  Sequenciador de segmentos      │  selecionado      │
└────────────┴─────────────────────────────────┴───────────────────┘
```

### Header

Contém os controles globais da sessão:

- **Abas de estado** — Cada aba representa um grupo de sirenes (ex.: `1.Emergency`, `2.Park`). Clique para alternar, duplo clique para renomear, `×` para excluir.
- **+ Estado** — Adiciona um novo estado vazio.
- **⧉ Duplicar** — Copia o estado ativo com todos os seus materiais.
- **🎨 Cores** — Abre o gerenciador de referências de cor.
- **⚙️ Refs** — Abre o gerenciador de referências de propriedade.
- **↑ Importar ▾** — Menu com opções de importação (`.json` ou `.jsonc`).
- **↓ Exportar ▾** — Menu com opções de exportação (`.json` ou `.jsonc`).
- **Seletor de idioma** — Alterna o idioma da interface (PT / EN / ES / RU / UK).

---

## Sistema de Estados

Um **estado** representa um modo de operação do veículo. Por exemplo:

| Estado | Uso típico |
|---|---|
| `1.Emergency` | Luzes de emergência completas ativas |
| `2.Park` | Modo estacionado, pisca lento |
| `3.Scene` | Iluminação de cena com luzes brancas fixas |

Cada estado possui seu próprio conjunto de materiais, independente dos demais. O jogador alterna entre estados usando teclas de atalho configuradas no mod.

**Operações disponíveis:**
- Adicionar estado em branco
- Renomear (duplo clique na aba)
- Duplicar estado ativo (copia todos os materiais)
- Excluir estado (requer ao menos 1 restante)

---

## Sistema de Materiais

Cada **material** corresponde a um slot de LED no modelo 3D do veículo — identificado por um número (1 a 255) que deve coincidir com o nome do dummy/material no modelo.

### Sidebar (lista de materiais)

Cada item na lista exibe:
- **Swatch de cor** — bolinha com a cor do LED
- **ID editável** — número clicável; altere e confirme para renomear o material
- **Label** — cor, referência de propriedade e ícone de rotator (se houver)
- **Indicador de estado** — bolinha verde que pulsa quando o LED está ON
- **👁 Ocultar no preview** — aparece ao passar o mouse; veja seção dedicada abaixo
- **✕ Excluir**

### Botões de rodapé da sidebar
- **+ Material** — Adiciona novo material com valores padrão
- **⧉** — Duplica o material selecionado

---

## Preview Grid (Grade de Preview)

A grade exibe quadrados numerados que representam cada material. A animação roda em tempo real, mostrando exatamente o comportamento que os LEDs terão no jogo.

- **Cor e brilho** — cada quadrado acende com a cor e intensidade do material
- **Número + tempo** — mostra o ID e a duração do segmento atual em ms
- **Agulha giratória** — materiais do tipo Rotator exibem uma agulha animada indicando o ângulo atual
- **Seleção** — clicar num quadrado seleciona o material para edição

### Controles do preview
- **ZOOM** — slider para ajustar o tamanho dos quadrados (32px a 76px)
- **⏸ Pausar / ▶ Play** — congela ou retoma a animação

---

## Timeline

A timeline exibe uma linha por material, com blocos coloridos representando a sequência de segmentos ON/OFF.

- **Blocos coloridos** = segmento ON (LED aceso), com a cor do material
- **Blocos escuros** = segmento OFF (LED apagado)
- **Largura proporcional** = visualmente proporcional à duração em ms
- **Clique** = seleciona o segmento para edição nas propriedades
- **+** ao final de cada linha = adiciona novo segmento

**Materiais Rotator** exibem uma barra especial em vez de segmentos, mostrando direção, velocidade e ângulo de rotação.

**MS padrão** — campo no topo da timeline que define a duração usada ao adicionar novos segmentos com o botão `+`.

---

## Painel de Propriedades

Exibe e edita todos os parâmetros do material selecionado. Todas as edições são refletidas imediatamente no preview.

### Cor
Dropdown com as cores nomeadas nas referências. A swatch ao lado mostra a cor atual com seus valores RGBA. O link "✏️ editar cores" abre o modal de referências de cor.

### Estado Inicial
Toggle ON / OFF — define se o LED começa aceso ou apagado ao iniciar o ciclo.

### Size / Inertia
Dois modos:

**Manual** — campos `Size` (tamanho do corona/LED) e `Inertia` (suavidade de transição). Inertia é opcional.

**Referência** — vincula o material a uma referência de propriedade nomeada (ex.: `strobe`, `strobe1`). Os valores de size/inertia vêm do objeto de referência, facilitando manter consistência entre materiais.

### Shadow
Checkbox para ativar. Quando ativo, exibe:
- **Offset** — deslocamento da sombra
- **Size** — tamanho da sombra
- **Texture** — nome da textura (ex.: `comet`, `pointlight`)

### Rotator
Checkbox para ativar o modo de rotação. Quando ativo:
- **Direção** — `clockwise` (horário), `counter-clockwise` (anti-horário), `switch` (vai e volta)
- **Speed (ms)** — tempo em milissegundos para completar um ciclo de rotação
- **Radius (°)** — ângulo total percorrido (ex.: 360 para rotação completa, 90 para varredura de 90°)
- **Offset (°)** — ângulo inicial (ex.: -45 para começar a -45° e ir até +45° no modo switch)
- **Type** — tipo de interpolação (`linear`)

> **Nota:** Materiais com Rotator ativado **não possuem Pattern** — o "tempo" é definido pelo campo Speed. A sincronização de piscar é substituída pela animação de rotação.

### Pattern (Padrão de piscar)
Lista de segmentos alternados ON/OFF. O estado do primeiro segmento é determinado pelo **Estado Inicial**.

Exemplo: estado inicial OFF, pattern `[300, 300]` → apagado 300ms, aceso 300ms, repete.

Exemplo complexo: estado inicial OFF, pattern `[50, 50, 50, 50, 50, 300]` → sequência de pulsos rápidos seguida de pausa longa.

**Operações:**
- Editar a duração de cada segmento (campo numérico)
- Excluir segmentos individuais (✕)
- Adicionar segmentos (botão ou + na timeline)
- Limpar todos os segmentos (pattern `[]` = LED estático, no estado definido pelo Estado Inicial)

> **Scroll da roda do mouse** em qualquer campo numérico: ajusta o valor. Shift = ±50, Ctrl = ±10, normal = ±1.

### JSON deste material
Caixa no final do painel que exibe o JSON correspondente ao material selecionado, no formato pronto para copiar e colar. Atualiza automaticamente conforme edições.

---

## Referências de Cor

Acessado via **🎨 Cores** no header. Permite criar e editar uma paleta de cores nomeadas que são usadas por todos os materiais.

Cada cor tem:
- **Nome** — identificador usado nos materiais (ex.: `red`, `blue`, `white`, `orange`)
- **R, G, B, A** — valores 0–255
- **Picker rápido** — seletor de cor nativo do navegador (aplica automaticamente RGB sem alterar Alpha)

**Por que usar referências de cor?** Se você precisar ajustar a tonalidade do vermelho em 30 materiais, basta editar a referência `red` uma vez — todos os materiais que a usam são atualizados automaticamente.

---

## Referências de Propriedade

Acessado via **⚙️ Refs** no header. Permite criar grupos de propriedades nomeados e reutilizáveis.

Exemplo de referência `strobe`:
```json
{
  "size": 0.4,
  "inertia": 0.5
}
```

Exemplo de referência `rotator`:
```json
{
  "size": 0.2,
  "state": 1,
  "type": "rotator",
  "rotator": { "direction": "clockwise", "type": "linear", "time": 500 }
}
```

**Operações:**
- Adicionar nova referência
- Adicionar/renomear/excluir campos individuais
- Renomear chaves de campo (a chave é um input editável)

---

## Ocultar Materiais no Preview

Com muitos materiais (até 255), pode ser difícil focar nos que estão sendo editados no momento. O botão **👁** (aparece ao passar o mouse em cada material na sidebar) permite ocultar materiais do preview.

**O que é afetado:**
- **Preview grid** — o material desaparece da grade animada
- **Timeline** — a linha do material fica dimmed (35% de opacidade)
- **Sidebar** — o item fica com 45% de opacidade, label riscado e badge `HIDDEN`

**O que NÃO é afetado:**
- Export `.json` e `.jsonc` — os materiais ocultos são sempre exportados normalmente
- Seleção e edição — você ainda pode selecionar e editar um material oculto

**Avisos:**
- Banner no topo do preview grid informa quantos materiais estão ocultos
- Botão **👁 mostrar todos** no header da sidebar e no banner do preview restaura tudo de uma vez
- O botão `🙈` no material oculto fica sempre visível (não precisa hover) para facilitar reativação

> **Atenção:** Ocultar é uma configuração de sessão apenas. Se exportar com materiais ocultos, o arquivo final estará completo — o export nunca é afetado.

---

## Import e Export

### Exportar .json
Gera um arquivo JSON puro com a estrutura `{ references, states }` — compatível com mods que leem diretamente o formato AVS/sirenes.

### Exportar .jsonc
Gera um arquivo `.jsonc` no formato do **Model Extras**:
- Se o arquivo foi importado de um `.jsonc`, reconstrói o arquivo original completo (`metadata`, `lights`, `carcols`, etc.) com o bloco `sirens` atualizado — os outros blocos são preservados intactos.
- Se o projeto foi criado do zero, gera um `.jsonc` mínimo com cabeçalho `metadata` básico.

### Importar .json
Lê um arquivo JSON com estrutura `{ references, states }` e carrega o projeto no editor.

### Importar .jsonc
Lê um arquivo `.jsonc` do Model Extras, suportando:
- Comentários `//` em qualquer posição
- Vírgulas finais (trailing commas) antes de `}` e `]`
- Extração automática do bloco `sirens`, preservando o restante do arquivo em memória para reexport
- **Cor inline** — materiais com `"color": { "red": 255, ... }` têm a cor automaticamente adicionada às referências de cor
- **Direction numérico** — valores `0`, `1`, `2` no campo `direction` do rotator são normalizados para `"clockwise"`, `"counter-clockwise"`, `"switch"`
- **Campo `time`** no rotator é automaticamente mapeado para `speed`

---

## Sincronização de Materiais

Materiais com o mesmo `patternTotal` (soma de todos os ms do pattern) são **automaticamente sincronizados** — quando qualquer um deles completa um ciclo, todos os outros com o mesmo total são reiniciados juntos.

Isso é o comportamento do mod e é refletido fielmente no preview. Para criar efeitos de alternância (vermelho e azul alternados), configure dois materiais com o mesmo pattern total mas estados iniciais opostos (um ON, um OFF).

---

## Formato JSON de Saída

```json
{
    "references": {
        "colors": {
            "red":   { "red": 255, "green": 20,  "blue": 20,  "alpha": 150 },
            "blue":  { "red": 51,  "green": 102, "blue": 255, "alpha": 150 },
            "white": { "red": 255, "green": 255, "blue": 255, "alpha": 128 }
        },
        "strobe": { "size": 0.4, "inertia": 0.5 }
    },
    "states": {
        "1.Emergency": {
            "1": {
                "color": "red",
                "state": 0,
                "pattern": [300, 300],
                "size": 0.4
            },
            "2": {
                "color": "red",
                "state": 1,
                "pattern": [300, 300],
                "size": 0.4
            },
            "3": {
                "color": "white",
                "state": 1,
                "reference": "strobe",
                "rotator": {
                    "direction": "clockwise",
                    "type": "linear",
                    "speed": 1000,
                    "radius": 360,
                    "offset": 0
                }
            }
        }
    }
}
```

### Regras do formato

| Campo | Tipo | Descrição |
|---|---|---|
| `color` | string | Nome de uma referência de cor |
| `state` | 0 ou 1 | Estado inicial: 0 = OFF, 1 = ON |
| `pattern` | array de números | Durações em ms, alternando ON/OFF a partir do estado inicial. Vazio = estático. |
| `size` | número | Tamanho do corona/LED |
| `inertia` | número | Suavidade de transição (opcional) |
| `reference` | string | Nome de uma referência de propriedade (substitui size/inertia) |
| `shadow.offset` | número | Deslocamento da sombra |
| `shadow.size` | número | Tamanho da sombra |
| `shadow.type` | string | Nome da textura da sombra (ex.: `"comet"`) |
| `rotator.direction` | string | `"clockwise"`, `"counter-clockwise"` ou `"switch"` |
| `rotator.speed` | número | Ms por ciclo de rotação |
| `rotator.radius` | número | Graus percorridos por ciclo |
| `rotator.offset` | número | Ângulo inicial em graus |
| `rotator.type` | string | `"linear"` |

> Materiais com `rotator` **não exportam** o campo `pattern`.

---

## Idiomas Suportados

A interface está disponível em 5 idiomas, selecionáveis no canto superior direito:

| Bandeira | Código | Idioma |
|---|---|---|
| 🇧🇷 | PT | Português (padrão) |
| 🇺🇸 | EN | English |
| 🇪🇸 | ES | Español |
| 🇷🇺 | RU | Русский |
| 🇺🇦 | UK | Українська |

A troca de idioma é instantânea e afeta todos os textos da interface, incluindo tooltips, avisos e labels das propriedades.

---

## Dicas de Uso

**Alternância vermelho/azul clássica:**
Crie dois materiais com a mesma cor vermelha e dois com azul. Configure o mesmo pattern em todos (ex.: `[300, 300]`). Defina estado inicial 0 em um vermelho e em um azul, e estado 1 no outro vermelho e no outro azul. Os quatro vão sincronizar e alternar em perfeita oposição.

**Padrão de pulso rápido (wig-wag):**
Pattern `[50, 50, 50, 50, 50, 300, 50, 50, 50, 50, 50, 300]` — cinco pulsos rápidos, pausa, repete.

**LED estático (farol de cena):**
Pattern `[]` (vazio) + Estado inicial 1 = LED sempre aceso, sem piscar.

**Rotator de varredura (não gira 360°):**
Rotator com `direction: switch`, `radius: 90`, `offset: -45` — a agulha varre de -45° a +45° e volta.

**Focar num grupo de materiais:**
Oculte todos os materiais que não estão sendo editados no momento usando o botão 👁. O preview mostrará somente os materiais relevantes, sem afetar o arquivo de saída.

**Ajuste fino de ms com scroll:**
Com o cursor sobre qualquer campo numérico, role a roda do mouse para ajustar o valor. Segure Shift para pulos de 50ms ou Ctrl para pulos de 10ms.

**Importar .jsonc de veículo existente:**
Importe o arquivo `.jsonc` do veículo diretamente. O editor carrega apenas o bloco `sirens` para edição. Ao exportar como `.jsonc`, o arquivo original é reconstruído com todas as outras seções (`metadata`, `lights`, `carcols`...) preservadas — você pode substituir diretamente o arquivo no jogo.

---

## Requisitos Técnicos

- Qualquer navegador moderno (Chrome, Firefox, Edge, Opera)
- Sem instalação, sem internet, sem dependências externas
- Arquivo único `.html` — pode ser guardado em qualquer pasta e aberto diretamente

---

*Desenvolvido como ferramenta de apoio para modders de GTA San Andreas.*
