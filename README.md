# Humanizer-BR — Editor de Texto Anti-IA

Skill para Claude Code que remove marcas típicas de textos gerados por IA, deixando a escrita mais natural, clara e próxima da linguagem humana. Inclui também o módulo **aprofundador** para aumentar a densidade intelectual do conteúdo.

---

## Instalação

### Método 1: Clonar direto no diretório de skills

```bash
git clone https://github.com/carlosafjr-dev/humanizer-br.git ~/.claude/skills/humanizer-br
```

### Método 2: Instalação manual

Copie os arquivos `SKILL.md` de cada skill para o diretório correto:

```bash
mkdir -p ~/.claude/skills/humanizer-br
cp skills/humanizer-br/SKILL.md ~/.claude/skills/humanizer-br/

mkdir -p ~/.claude/skills/aprofundador
cp skills/aprofundador/SKILL.md ~/.claude/skills/aprofundador/
```

### Método 3: Instalação manual no claude.ia

Baixe o zip do arquivo e descompacte no seu computador 

Vá em claude.ai 

Configurações > Capacidades > Habilidades > Clica no + > + Criar habilidade > Fazer upload de uma habilidade

Selecione a pasta onde você descompactou a skill. Existe a pasta skills e dentro dela duas pastas: 'aprofundador' e 'humanizer-br'

Vá primeiro na pasta 'humanizer-br'e selecione a 'SKILL.md' que está dentro dela. Faça o mesmo com a pasta 'aprofundador'.

### Método 4: Script automático (Windows PowerShell)

Crie um script `install.ps1` com:

```powershell
$skillsDir = "$env:USERPROFILE\.claude\skills"
mkdir -p $skillsDir/humanizer-br
mkdir -p $skillsDir/aprofundador
cp skills/humanizer-br/SKILL.md $skillsDir/humanizer-br/
cp skills/aprofundador/SKILL.md $skillsDir/aprofundador/
```

---

## Uso

### Humanizer-BR

Remove padrões de escrita gerada por IA:

```
/humanizer-br

[cole seu texto aqui]
```

### Aprofundador

Aumenta a densidade intelectual do texto (use após o humanizer):

```
/aprofundador

[cole o texto já humanizado aqui]
```

### Pipeline recomendado

1. **Texto Base** (IA ou rascunho)
2. **Humanizer-BR** (remove marcas de IA)
3. **Aprofundador** (aprofunda o conteúdo)
4. **Editor Final** (ajuste de fluidez e estilo)

Você pode pedir ao Claude para aplicar ambas em sequência:

> "Aplique o humanizer-br neste texto e depois use o aprofundador."

---

## Visão Geral

O Humanizer-BR é baseado em três referências principais:

- **Wikipedia: Signs of AI Writing** — guia da comunidade para identificar textos gerados por IA
- **Sampaio, R.C. (2026)** — Prompts para diminuir os marcadores de escrita por IA
- **Floridi, L. (2025)** — Distant Writing: Literary Production in the Age of AI

A skill analisa mais de 150 palavras e expressões típicas de IA, estruturas gramaticais problemáticas e padrões de pontuação, reescrevendo o texto para eliminar sinais artificiais e melhorar naturalidade.

### Por que textos de IA são detectáveis?

LLMs usam algoritmos estatísticos para prever o que provavelmente vem em seguida em um texto. O resultado tende a convergir para construções que funcionam na maior variedade possível de contextos, gerando:

- Frases genéricas
- Estruturas previsíveis
- Vocabulário inflado e vago
- Conclusões amplas sem dados concretos

---

## Padrões detectados

### Padrões de conteúdo

**1. Inflação de importância**

Amplia artificialmente a relevância de algo com expressões grandiosas.

> Antes: "marcando um momento decisivo na evolução de..."
> Depois: "foi criado em 1989 para coletar estatísticas regionais"

**2. Name-dropping de notoriedade**

Lista veículos de imprensa para criar autoridade sem contexto.

> Antes: "citado pelo NYT, BBC, FT e The Hindu"
> Depois: "Em entrevista ao NYT em 2024, ela afirmou..."

**3. Análises superficiais com gerúndio**

Frases com gerúndio que fingem profundidade sem entregar conteúdo.

> Antes: "simbolizando... refletindo... demonstrando..."
> Depois: Remover ou expandir com fatos concretos

**4. Linguagem promocional**

Adjetivos exagerados que parecem texto de marketing.

> Antes: "localizado em uma região deslumbrante"
> Depois: "é uma cidade da região de Gonder"

**5. Atribuições vagas**

Cita "especialistas" sem nome, data ou fonte.

> Antes: "Especialistas acreditam que..."
> Depois: "Segundo pesquisa de 2019 realizada por..."

**6. Fórmula genérica de desafios**

Reconhece problemas de forma vaga para depois ignorá-los.

> Antes: "Apesar dos desafios, continua prosperando"
> Depois: Descrever desafios reais

---

### Padrões de linguagem

**7. Vocabulário típico de IA**

Palavras que aparecem com frequência exagerada em textos de IA.

> Antes: "testemunho de, crucial, paisagem"
> Depois: Termos mais diretos e concretos

**8. Evitar verbo "ser"**

Troca verbos simples por construções elaboradas desnecessárias.

> Antes: "serve como... apresenta..."
> Depois: "é... tem..."

**9. Paralelismo negativo**

Estrutura forçada de negação para criar contraste artificial.

> Antes: "Não é apenas X, é Y"
> Depois: Afirmar diretamente

**10. Regra artificial de três**

LLMs agrupam ideias em listas mecânicas de três itens.

> Antes: "inovação, inspiração e insights"
> Depois: Usar número natural de itens

**11. Rotação de sinônimos**

Troca palavras repetidas desnecessariamente para parecer variado.

> Antes: "protagonista... personagem principal..."
> Depois: Repetir o termo mais claro

**12. Intervalos artificiais**

Usa "de X a Y" sem uma escala lógica real.

> Antes: "do Big Bang à matéria escura"
> Depois: Listar diretamente

---

### Padrões de estilo

**13. Travessão excessivo**

Uso desnecessário de travessões para criar ênfase artificial.

> Antes: "instituições---não pessoas---"
> Depois: Usar vírgulas ou pontos

**14. Negrito excessivo**

Destaca palavras sem necessidade real.

> Antes: "**OKRs**, **KPIs**"
> Depois: "OKRs, KPIs"

**15. Listas com rótulo inline**

Estrutura mecânica de "rótulo: descrição" em listas.

> Antes: "**Performance:** melhorou"
> Depois: Converter em frase natural

**16. Títulos em Title Case**

Capitalização excessiva em títulos e cabeçalhos.

> Antes: "Strategic Negotiations And Partnerships"
> Depois: "Strategic negotiations and partnerships"

**17. Emojis**

Emojis em contextos editoriais ou profissionais.

> Antes: "🚀 Lançamento"
> Depois: Remover

**18. Aspas inconsistentes**

Mistura de estilos de aspas no mesmo texto.

> Antes: Misturar estilos
> Depois: Padronizar

---

### Padrões de comunicação

**19. Artefatos de chatbot**

Frases de cortesia que denunciam texto gerado por IA.

> Antes: "Espero que isso ajude!"
> Depois: Remover

**20. Avisos de limitação**

Chama atenção para a falta de informação em vez de buscar dados.

> Antes: "Detalhes são limitados nas fontes"
> Depois: Buscar fontes ou remover

**21. Tom bajulador**

Elogia o leitor ou a pergunta antes de responder.

> Antes: "Ótima pergunta!"
> Depois: Responder diretamente

---

### Preenchimento e hedging

**22. Frases de preenchimento**

Expressões longas que poderiam ser diretas.

> Antes: "Com o objetivo de"
> Depois: "Para"

**23. Hedging excessivo**

Acúmulo de palavras que enfraquecem a afirmação.

> Antes: "poderia possivelmente vir a"
> Depois: "Pode"

**24. Conclusões genéricas**

Fechamentos vagos que não agregam informação.

> Antes: "O futuro parece promissor"
> Depois: Usar fatos concretos

---

## Exemplo completo

### Antes (texto típico de IA)

> Ótima pergunta! Aqui está um resumo sobre este tema. Espero que isso ajude!
>
> A programação assistida por IA serve como um testemunho duradouro do potencial transformador dos grandes modelos de linguagem.
>
> O futuro parece promissor.

### Depois (texto humanizado)

Assistentes de código com IA ajudam principalmente nas partes repetitivas do trabalho.

Eles são bons para gerar boilerplate, arquivos de configuração e pequenos trechos de código.

O risco está na confiança que essas sugestões transmitem. Código pode compilar e ainda assim resolver o problema errado.

Quando usados como autocomplete e revisados linha por linha, são úteis. Sem testes automatizados, erros passam despercebidos.

---

## Estrutura do repositório

```
humanizer-br/
├── skills/
│   ├── humanizer-br/
│   │   └── SKILL.md          # Skill principal (anti-IA)
│   └── aprofundador/
│       └── SKILL.md          # Módulo complementar (densidade intelectual)
├── README.md
└── WARP.md
```

---

## Histórico de versões

### 2.0.0 (atual)
- Reestruturação completa baseada no guia da Wikipédia
- Vocabulário proibido expandido para ~150 palavras e expressões
- Seções de estruturas gramaticais proibidas (cópulas artificiais, paralelismos, regra de três, intervalos falsos, editorialização)
- Regras rigorosas de pontuação (travessão proibido, ponto e vírgula evitado)
- Teste Mental de Autenticidade com 3 perguntas de validação
- Referências acadêmicas adicionadas (Sampaio 2026, Floridi 2025)
- aprofundador integrado como módulo complementar

### 1.0.0
- Primeira versão pública

---

## Licença

Free
