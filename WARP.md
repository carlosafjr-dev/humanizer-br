# WARP.md

Este arquivo orienta editores e ferramentas ao trabalhar com o código deste repositório.

---

## O que é este repositório

Este repositório contém **duas skills do Claude Code** implementadas inteiramente em Markdown:

1. **humanizer-br** — Remove sinais de escrita gerada por IA
2. **density-booster** — Aumenta densidade intelectual do texto

Cada skill é definida por um arquivo `SKILL.md` dentro do diretório `skills/`.

---

## Estrutura de arquivos

```
humanizer-br/
├── skills/
│   ├── humanizer-br/
│   │   └── SKILL.md          # Skill principal
│   └── density-booster/
│       └── SKILL.md          # Módulo complementar
├── para-instalar/            # Cópia pronta para instalação
│   ├── install.ps1
│   ├── humanizer-br/SKILL.md
│   └── density-booster/SKILL.md
├── README.md                 # Documentação para humanos
└── WARP.md                   # Este arquivo
```

### SKILL.md

Define o comportamento real de cada skill. O Claude Code lê:

1. O **frontmatter YAML** (metadados: `name`, `version`, `description`)
2. O **prompt e instruções** após o frontmatter

Trate como **fonte de verdade da lógica de cada skill**.

### README.md

Documento voltado para usuários humanos. Inclui instalação, uso, padrões detectados e histórico de versões.

---

## Como instalar

### Método recomendado

```bash
git clone https://github.com/carlosafjr-dev/humanizer-br.git ~/.claude/skills/humanizer-br
```

### Instalação manual

```bash
mkdir -p ~/.claude/skills/humanizer-br
cp skills/humanizer-br/SKILL.md ~/.claude/skills/humanizer-br/

mkdir -p ~/.claude/skills/density-booster
cp skills/density-booster/SKILL.md ~/.claude/skills/density-booster/
```

---

## Como fazer alterações com segurança

### Controle de versão

Três arquivos precisam permanecer sincronizados:

- `skills/humanizer-br/SKILL.md`
- `skills/density-booster/SKILL.md`
- `README.md`

O campo `version:` no frontmatter YAML de cada SKILL.md deve ser atualizado no README.md sempre que houver mudanças.

### Ao editar SKILL.md

- Mantenha a formatação válida do YAML
- Preserve indentação correta
- Não altere a numeração dos padrões sem atualizar o README

### Documentando correções

Registre no histórico de versões do README:

- Correção de reescrita excessiva
- Mudanças no tom editorial
- Novos padrões de escrita artificial
- Falhas recorrentes observadas em textos reais
