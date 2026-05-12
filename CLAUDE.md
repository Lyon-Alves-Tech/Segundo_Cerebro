# CLAUDE.md — Writing Wiki: Segundo Cérebro para Pesquisa Acadêmica

> **Para o usuário:** este arquivo é lido pelo agente de IA (Claude/Cowork) no início
> de cada sessão. Preencha as seções marcadas com `[PREENCHER]` antes de começar a usar.
> Não renomeie este arquivo — o agente o procura por este nome exato.

---

## Identidade do projeto

**Autor:** [PREENCHER — seu nome]
**Título provisório:** [PREENCHER — título da tese/dissertação/livro]
**Instituição:** [PREENCHER — universidade e programa]
**Orientador/a:** [PREENCHER — se aplicável]
**Fase atual:** [PREENCHER — ex: pesquisa bibliográfica / escrita do cap. 2 / revisão pós-banca]

**Tese central em uma frase:**
[PREENCHER — uma frase que encapsule o argumento principal. Consulte [[tese/argumento-central]].]

---

## Estrutura da wiki

```
wiki/
├── index.md                  ← mapa de tudo (atualizar a cada mudança)
├── log.md                    ← registro cronológico append-only
├── tese/
│   ├── argumento-central.md  ← tese, hipótese, contribuição original ← COMECE AQUI
│   ├── cap1-introducao.md    ← Introdução
│   ├── cap2-[titulo].md      ← Capítulo 2
│   ├── [cap3...].md          ← demais capítulos conforme criados
│   └── lacunas.md            ← pontos em aberto e tensões
├── autores/
│   ├── autor-01.md           ← template de autor (renomear)
│   └── [outros conforme surgem]
├── conceitos/
│   ├── conceito-01.md        ← template de conceito (renomear)
│   └── [outros conforme surgem]
└── tensoes/
    ├── tensao-01.md          ← template de tensão (renomear)
    └── [outros conforme surgem]
```

---

## Convenções de página

### Páginas de autor
```markdown
# [Nome do Autor]
## Relevância para a tese
## Argumentos mobilizados
## Tensões com outros autores
## Lacunas / críticas internas
## Aparece em
```

### Páginas de conceito
```markdown
# [Conceito]
## Definição operativa na tese
## Origem filosófica
## Papel no argumento
## Relações com outros conceitos
## Pontos em aberto
```

### Páginas de capítulo
```markdown
# Capítulo X — [Título]
## Estado atual
## Função no argumento
## Argumento do capítulo
## O que está resolvido
## O que falta
## Tensões não resolvidas
## Conexões com a wiki
## Fontes principais
```

### Páginas de tensão
```markdown
# Tensão: [A] vs. [B]
## Natureza do conflito
## Como a tese se posiciona
## Resolução proposta
## Autores em cada polo
```

---

## Workflows

### Ingestão de fonte nova
Quando receber um artigo, livro, capítulo ou PDF:
1. Leia (ou solicite ao agente que leia) a fonte
2. Identifique: qual argumento da tese é afetado? qual conceito? qual tensão?
3. Escreva/atualize a página do autor correspondente
4. Atualize os conceitos tocados
5. Se contradiz algo já na wiki, registre na página de tensões relevante
6. Adicione entrada ao `log.md`
7. Atualize o `index.md` se criou arquivo novo

**Frase de acionamento para o agente:** *"ingestão desta fonte"* ou *"processa esse artigo na wiki"*

### Ingestão de anotação ou insight
Para fotos de anotações, notas do celular, insights de conversa:
1. Identifique a qual conceito ou capítulo pertence
2. Integre no local correto (não crie arquivo isolado a não ser que seja genuinamente novo)
3. Registre no `log.md`

**Frase de acionamento:** *"insight: [texto]"* ou *"integra essa anotação"*

### Ingestão de conversa de LLM
Para exports de conversas do Claude, ChatGPT ou similares:
1. Identifique os raciocínios relevantes (ignore o scaffolding da conversa)
2. Extraia argumentos, formulações, objeções respondidas
3. Integre nas páginas de capítulo ou conceito correspondentes
4. Marque com `[Desenvolvido em conversa — verificar com fontes]` quando não houver respaldo bibliográfico direto

**Frase de acionamento:** *"extrai o que importa dessa conversa para a wiki"*

### Query sobre a tese
Quando consultar o estado do argumento, de um capítulo ou de um conceito:
1. Leia o `index.md` para localizar as páginas relevantes
2. Leia as páginas identificadas
3. Sintetize com base no que está na wiki
4. Aponte explicitamente o que está em aberto ou insuficiente

**Frases de acionamento:** *"como está o cap. 2?"* / *"o que falta em [[conceitos/conceito-01]]?"*

### Lint (revisão de saúde da wiki)
Periodicamente, verificar:
- Links internos quebrados (arquivo mencionado que não existe)
- Páginas de autor sem conexão com capítulos
- Conceitos mencionados sem página própria
- Tensões não resolvidas que travam o argumento
- Contradições entre `argumento-central.md` e as páginas de capítulo

**Frase de acionamento:** *"roda um lint"* ou *"diagnóstico da wiki"*

---

## Contexto do argumento (para orientação do agente)

> **[PREENCHER]** — após configurar o projeto, preencha esta seção com um resumo
> do seu argumento em 3–5 parágrafos. O agente usa isso para orientar ingestões
> e queries sem precisar reler todos os arquivos a cada sessão.
>
> Estrutura sugerida:
> - O problema que a tese endereça
> - Por que as respostas existentes são insatisfatórias
> - O que a tese propõe
> - Os recursos teóricos principais
> - O estado atual dos capítulos

---

## Notas de terminologia

> **[PREENCHER]** — liste os termos técnicos do seu argumento e como devem ser usados.
> Isso evita inconsistências ao longo da escrita.
>
> Exemplo de formato:
> - **Termo canônico** (não "sinônimo impreciso" nem "expressão vaga")
> - **Outro termo** (não "equivalente que muda o sentido")

---

## Gestão do log e index

O agente deve manter:
- `log.md`: entrada a cada operação (ingestão, lint, reestruturação), com data e descrição
- `index.md`: lista de todas as páginas com link e uma linha de descrição

Formato do log:
```
## [YYYY-MM-DD] tipo | descrição breve
Resumo do que foi feito. Links para páginas afetadas.
```

---

## Prompt de abertura recomendado

No início de cada conversa nova com o agente, cole:

> *"Lê CLAUDE.md e wiki/index.md, depois me diz o estado da wiki em uma linha e aguarda instrução."*

Isso mantém o custo inicial baixo — o agente lê só o essencial e espera você definir o escopo.
