# MANUAL DE INSTALAÇÃO E CONFIGURAÇÃO
## Writing Wiki — Segundo Cérebro para Pesquisa Acadêmica

> **Este manual cobre tudo do zero:** instalação do Obsidian, configuração do vault,
> integração com Git, conexão ao Claude/Cowork e fluxo de trabalho diário.
> Tempo estimado para configuração inicial: **30–45 minutos**.

---

## Índice

1. [O que é este projeto](#1-o-que-é-este-projeto)
2. [Pré-requisitos](#2-pré-requisitos)
3. [Instalação do Obsidian](#3-instalação-do-obsidian)
4. [Configuração do vault](#4-configuração-do-vault)
5. [Plugins recomendados](#5-plugins-recomendados)
6. [Configuração do Git (versionamento)](#6-configuração-do-git-versionamento)
7. [Integração com Claude / Cowork](#7-integração-com-claude--cowork)
8. [Primeiros passos: configurar o projeto](#8-primeiros-passos-configurar-o-projeto)
9. [Fluxo de trabalho](#9-fluxo-de-trabalho)
10. [Comandos de referência rápida](#10-comandos-de-referência-rápida)
11. [Resolução de problemas](#11-resolução-de-problemas)
12. [Estrutura de arquivos explicada](#12-estrutura-de-arquivos-explicada)

---

## 1. O que é este projeto

Este repositório é um **template de segundo cérebro** para pesquisa acadêmica de escrita longa
(teses, dissertações, livros). Ele combina:

- **Obsidian** — editor de notas em Markdown com links internos, grafo de conhecimento e plugins
- **Estrutura wiki** — arquivos organizados por função: autores, conceitos, tensões, capítulos
- **Git** — versionamento do vault para histórico, rollback e backup em nuvem
- **Claude / Cowork** — agente de IA que lê, escreve e rastreia o estado do argumento

**O que este projeto NÃO é:**
- Um gerenciador de referências (use Zotero, Mendeley ou similar para isso)
- Um processador de texto (a escrita final acontece no Word, LibreOffice ou LaTeX)
- Um substituto para pensar — é uma ferramenta para pensar melhor

---

## 2. Pré-requisitos

Antes de começar, certifique-se de ter:

| Ferramenta | Obrigatório? | Download |
|---|---|---|
| Obsidian | ✅ Sim | https://obsidian.md |
| Git | ✅ Sim (para versionamento) | https://git-scm.com |
| Conta no GitHub/GitLab | Recomendado | https://github.com |
| Claude / Cowork | Recomendado | https://claude.ai |
| VSCode | Opcional | https://code.visualstudio.com |

**Sistema operacional:** Windows, macOS ou Linux. O template funciona em todos.

---

## 3. Instalação do Obsidian

### 3.1 Download e instalação

1. Acesse https://obsidian.md e clique em **Download**
2. Escolha a versão para o seu sistema operacional
3. Execute o instalador e siga as instruções
4. Na primeira abertura, o Obsidian perguntará se quer criar um vault novo ou abrir um existente

### 3.2 Abrir o vault do template

Após baixar ou clonar este repositório:

1. Na tela inicial do Obsidian, clique em **"Open folder as vault"**
2. Navegue até a pasta `writing-wiki/` (a pasta que contém `CLAUDE.md` e a subpasta `wiki/`)
3. Clique em **Open**

> ⚠️ **Importante:** abra a pasta `writing-wiki/` como vault, não a pasta `wiki/` dentro dela.
> O Obsidian precisa da pasta raiz para encontrar o arquivo `.obsidian/`.

### 3.3 Confirmar que o vault abriu corretamente

No painel esquerdo do Obsidian você deve ver:
```
writing-wiki/
├── CLAUDE.md
├── MANUAL.md
└── wiki/
    ├── index.md
    ├── log.md
    ├── autores/
    ├── conceitos/
    ├── tensoes/
    └── tese/
```

Se a estrutura aparecer corretamente, o vault está configurado.

---

## 4. Configuração do vault

### 4.1 Configurações essenciais do Obsidian

Acesse **Settings** (ícone de engrenagem no canto inferior esquerdo) e configure:

#### Files & Links
- **Default location for new notes:** escolha `wiki/` ou uma subpasta específica
- **Use [[Wikilinks]]:** ✅ ativado (necessário para os links internos funcionarem)
- **Automatically update internal links:** ✅ ativado (renomear arquivos atualiza links)

#### Editor
- **Default editing mode:** Live Preview (recomendado para iniciantes) ou Source (para power users)
- **Spell check:** ative e configure para o seu idioma

#### Appearance
- **Theme:** escolha qualquer tema — recomendamos **Minimal** ou **Things** para leitura longa

### 4.2 Configurar a pasta raiz de novas notas

Para que novas notas sejam criadas dentro de `wiki/` por padrão:

1. Settings → Files & Links
2. **Default location for new notes:** "In the folder specified below"
3. **Folder to create new notes in:** `wiki`

---

## 5. Plugins recomendados

### 5.1 Plugins nativos (já incluídos no Obsidian)

Ative em Settings → Core Plugins:

| Plugin | Para que serve | Ativar? |
|---|---|---|
| Backlinks | Mostra quem linka para a nota atual | ✅ Sim |
| Graph view | Visualiza a rede de notas | ✅ Sim |
| Outline | Mostra o índice da nota atual | ✅ Sim |
| Templates | Cria notas a partir de templates | ✅ Sim |
| Search | Busca por conteúdo em todo o vault | ✅ Sim |
| File recovery | Versões automáticas dos arquivos | ✅ Sim |

### 5.2 Plugins da comunidade (instalação manual)

Acesse Settings → Community Plugins → Browse e instale:

#### Dataview ⭐ (muito recomendado)
Permite fazer consultas dinâmicas ao vault. Exemplos:
- "Liste todos os autores cujas páginas não têm seção 'Fontes'"
- "Mostre todos os conceitos com pontos em aberto"

**Instalação:** Community Plugins → Browse → buscar "Dataview" → Install → Enable

**Uso básico:**
````markdown
```dataview
LIST
FROM "wiki/autores"
WHERE !contains(file.name, "template")
SORT file.name ASC
```
````

#### Templater (recomendado)
Permite templates mais poderosos com variáveis de data, nome do arquivo, etc.

**Instalação:** Community Plugins → Browse → buscar "Templater" → Install → Enable

**Configuração:**
1. Settings → Templater
2. **Template folder location:** crie uma pasta `_templates/` no vault e aponte para ela

#### Calendar (opcional)
Adiciona um calendário no painel lateral com acesso rápido a notas diárias.

**Instalação:** Community Plugins → Browse → buscar "Calendar" → Install → Enable

#### Advanced Tables (opcional)
Facilita a criação e edição de tabelas em Markdown.

**Instalação:** Community Plugins → Browse → buscar "Advanced Tables" → Install → Enable

### 5.3 Configurar os templates

Se instalou o plugin **Templates** nativo:

1. Settings → Templates
2. **Template folder location:** crie uma pasta `_templates/` no vault

Os templates de autores, conceitos e tensões incluídos neste projeto (em `wiki/autores/autor-01.md`, etc.) já funcionam como modelos — você pode copiá-los manualmente. O plugin Templates permite inserir esses modelos com um atalho de teclado.

---

## 6. Configuração do Git (versionamento)

O Git permite desfazer qualquer mudança, ver o histórico completo do vault e fazer backup na nuvem.

### 6.1 Verificar se o Git está instalado

**Windows (PowerShell ou Prompt de Comando):**
```powershell
git --version
```

Se aparecer `git version X.X.X`, está instalado. Se não, baixe em https://git-scm.com.

**macOS/Linux (Terminal):**
```bash
git --version
```

### 6.2 Inicializar o repositório Git

Navegue até a pasta raiz do vault (onde está o `CLAUDE.md`) e execute:

**Windows (PowerShell):**
```powershell
cd C:\caminho\para\writing-wiki
git init
git add .
git commit -m "setup: inicialização da wiki"
```

**macOS/Linux (Terminal):**
```bash
cd /caminho/para/writing-wiki
git init
git add .
git commit -m "setup: inicialização da wiki"
```

### 6.3 Conectar ao GitHub (backup em nuvem)

1. Crie um repositório no GitHub em https://github.com/new
   - **Importante:** se o vault contém rascunhos de pesquisa que não quer tornar públicos, crie o repositório como **Privado**
   - Não marque "Add a README file" (já temos um)

2. Conecte o repositório local ao GitHub:

```bash
git remote add origin https://github.com/SEU-USUARIO/NOME-DO-REPO.git
git branch -M main
git push -u origin main
```

3. Para enviar atualizações futuras:
```bash
git add .
git commit -m "descrição do que mudou"
git push
```

### 6.4 Comandos do dia a dia

| Intenção | Comando |
|---|---|
| Ver o que mudou | `git status` |
| Ver as diferenças linha a linha | `git diff` |
| Salvar o estado atual | `git add . && git commit -m "mensagem"` |
| Enviar para o GitHub | `git push` |
| Desfazer mudanças não commitadas | `git reset --hard HEAD` |
| Ver histórico de commits | `git log --oneline` |
| Voltar a um commit anterior | `git reset --hard <hash-do-commit>` |

### 6.5 Quando fazer commits

- **Antes** de qualquer operação grande do agente (ingestão densa, reestruturação)
- **Depois** de cada sessão de escrita produtiva
- **Sempre** antes de renomear arquivos ou conceitos em massa

**Sugestão de mensagens de commit:**
```
"cap2: primeira versão do argumento do capítulo"
"conceitos: página de [conceito] preenchida"
"lint: links quebrados corrigidos"
"ingestão: [Autor, Obra]"
```

### 6.6 Plugin Git para Obsidian (opcional)

Para fazer commits diretamente do Obsidian sem abrir o terminal:

**Instalação:** Community Plugins → Browse → buscar "Obsidian Git" → Install → Enable

**Configuração básica:**
1. Settings → Obsidian Git
2. **Vault backup interval (minutes):** 30 (faz commit automático a cada 30min)
3. **Auto pull interval (minutes):** 10 (sincroniza com o GitHub)

---

## 7. Integração com Claude / Cowork

O agente de IA lê os arquivos do vault e ajuda a ingerir fontes, diagnosticar lacunas e rastrear o argumento.

### 7.1 O que o agente pode fazer

| Tarefa | Como pedir |
|---|---|
| Ingerir artigo/PDF | Anexe o arquivo e diga *"ingestão desta fonte"* |
| Ingerir anotação manuscrita (foto) | Anexe a foto e diga *"integra essa anotação na wiki"* |
| Ingerir conversa de LLM | Cole o texto e diga *"extrai o que importa para a wiki"* |
| Verificar estado do argumento | *"como está o cap. 2?"* ou *"o que falta em [[conceitos/X]]?"* |
| Diagnóstico completo | *"roda um lint"* ou *"diagnóstico da wiki"* |
| Rascunhar página nova | *"esboça a página de [autor X]"* |
| Revisar trecho | *"revisa esse parágrafo como crítico sincero"* |
| Conectar pontos | *"qual a relação entre X e Y no argumento?"* |

### 7.2 Configurar o agente para o seu projeto

**No Claude/Cowork:**
1. Abra o Cowork (Claude desktop)
2. Clique em **"Select folder"** e selecione a pasta `writing-wiki/`
3. No início de cada conversa nova, use este prompt de abertura:

```
Lê CLAUDE.md e wiki/index.md, depois me diz o estado da wiki em uma linha e aguarda instrução.
```

Isso garante que o agente leia o contexto mínimo antes de qualquer tarefa.

### 7.3 Prompt de abertura explicado

O prompt `"Lê CLAUDE.md e wiki/index.md..."` faz o agente:
- Ler o `CLAUDE.md` (identidade do projeto, convenções, contexto do argumento)
- Ler o `index.md` (mapa de todas as páginas)
- Reportar o estado atual em uma linha
- **Aguardar sua instrução** sem tomar iniciativa

Sem esse prompt, o agente pode antecipar tarefas e ler arquivos desnecessários, consumindo mais tokens.

### 7.4 Economia de tokens (importante)

Tokens são a "moeda" de processamento do agente — cada leitura de arquivo tem custo.

**Práticas para reduzir custo:**

1. **Seja específico:** em vez de "vamos trabalhar na tese", diga "estou no cap. 2, seção sobre [X]"
2. **Use nomes canônicos dos arquivos:** `[[autores/nome]]` em vez de "a página do fulano"
3. **Cole trechos curtos** (< 50 linhas) em vez de pedir ao agente para ler o arquivo
4. **Abra conversa nova** quando mudar de tópico (cap. 2 → cap. 4)
5. **Consolide antes de fechar:** ao final da sessão, peça *"consolida o que decidimos hoje"*
6. **Mande texto longo em blocos:** para revisão de capítulos, envie seção por seção

### 7.5 O que o agente NÃO deve fazer

- ❌ Escrever o capítulo por você — ele rascunha, sugere, critica; a voz é sua
- ❌ Criar páginas de insight isoladas quando o conteúdo cabe em um conceito existente
- ❌ Ingerir uma fonte sem que você a tenha ao menos resumido/lido o abstract
- ❌ Editar arquivos enquanto você está editando os mesmos no Obsidian

---

## 8. Primeiros passos: configurar o projeto

Depois de instalar o Obsidian e (opcionalmente) o Git, siga esta sequência:

### Passo 1: Preencher o CLAUDE.md

Abra `CLAUDE.md` e preencha todas as seções marcadas com `[PREENCHER]`:

- Nome, título provisório, instituição, orientador/a, fase atual
- Tese central em uma frase (mesmo que ainda seja rascunho)
- Contexto do argumento (3–5 parágrafos)
- Terminologia canônica do seu campo

**Isso leva ~20 minutos e é o investimento mais importante da configuração.**

### Passo 2: Preencher o argumento central

Abra `wiki/tese/argumento-central.md` e preencha o que você já sabe:
- Tese em uma frase
- O problema
- O diagnóstico (crítica às respostas existentes)
- A proposta (mesmo que ainda seja incompleta)

Não precisa estar pronto — precisa estar honesto sobre o estado atual.

### Passo 3: Renomear e preencher os templates

Para cada autor, conceito e tensão do seu projeto:

1. Copie o arquivo template (`autor-01.md`, `conceito-01.md`, `tensao-01.md`)
2. Renomeie para o nome correto em kebab-case (ex: `kant.md`, `sujeito-moral.md`)
3. Preencha as seções relevantes

Não precisa preencher tudo de uma vez — escreva o que sabe agora e complemente conforme avança.

### Passo 4: Preencher os capítulos

Abra `wiki/tese/cap1-introducao.md` e `wiki/tese/cap2-primeiro-capitulo.md`:
- Defina o **título** de cada capítulo
- Preencha a **função no argumento** (uma frase: "este capítulo faz X")
- Liste o que está **resolvido** e o que **falta**

Para capítulos adicionais, copie o template `cap2-primeiro-capitulo.md` e renomeie.

### Passo 5: Atualizar o index.md

Abra `wiki/index.md` e atualize os links para refletir os arquivos que você criou:
- Substitua `autor-01`, `autor-02` pelos nomes reais
- Adicione linhas para todos os capítulos, conceitos e tensões do seu projeto

### Passo 6: Registro inicial no log

Abra `wiki/log.md` e escreva a primeira entrada:

```markdown
## [DATA DE HOJE] setup | Inicialização da wiki

Wiki configurada a partir do template `writing-wiki`.
Projeto: [título provisório].
Estado inicial: [o que já existe / qual fase da pesquisa].
```

### Passo 7: Fazer o primeiro commit Git (se usando Git)

```bash
git add .
git commit -m "setup: configuração inicial do projeto [título]"
```

---

## 9. Fluxo de trabalho

### Sessão diária (30–60 min)

```
1. Abrir Obsidian — navegar para o capítulo/conceito em foco
2. Trabalhar manualmente o que você já sabe escrever
3. Quando travar ou precisar de revisão → ir ao Cowork:
   "trabalhando [[tese/cap2]], estou com [dúvida específica]"
4. Antes de fechar → atualizar o log:
   "atualiza o log com o que fizemos hoje"
5. Commit Git:
   git add . && git commit -m "cap2: [o que avançou]"
```

### Sessão de ingestão (leitura nova)

```
1. Ler o artigo/capítulo (você mesmo — pelo menos o abstract e a conclusão)
2. No Cowork: anexar o PDF ou colar o texto
3. Dizer: "ingestão desta fonte"
4. O agente segue o workflow do CLAUDE.md e atualiza a wiki
5. Você revisa as mudanças no Obsidian (graph view mostra o impacto)
6. Se algo ficou mal integrado: pedir ajuste
```

### Auditoria mensal (lint)

```
1. No Cowork: "roda lint completo da wiki"
2. O agente reporta:
   - Links quebrados
   - Páginas de autor sem conexão com capítulos
   - Conceitos mencionados sem página
   - Contradições entre argumento-central e capítulos
3. Atacar em ordem: contradições > lacunas prioritárias > órfãos
4. Atualizar tese/lacunas.md com o diagnóstico
5. Commit: "lint: diagnóstico mensal [data]"
```

---

## 10. Comandos de referência rápida

### Obsidian

| Ação | Atalho |
|---|---|
| Criar nota nova | `Ctrl+N` (Windows/Linux) / `Cmd+N` (macOS) |
| Abrir nota por nome | `Ctrl+O` / `Cmd+O` |
| Busca em todo o vault | `Ctrl+Shift+F` / `Cmd+Shift+F` |
| Inserir link interno | `[[` + nome do arquivo |
| Abrir graph view | `Ctrl+G` / `Cmd+G` |
| Toggle preview/edit | `Ctrl+E` / `Cmd+E` |

### Git (PowerShell/Terminal, dentro da pasta do vault)

```bash
# Ver estado atual
git status

# Salvar ponto de checkpoint
git add . && git commit -m "checkpoint antes de [operação]"

# Desfazer mudanças não salvas
git reset --hard HEAD

# Ver histórico
git log --oneline

# Voltar a commit anterior
git reset --hard <hash>

# Enviar para GitHub
git push
```

### Frases de acionamento para o agente

| Intenção | Frase |
|---|---|
| Ingestão de fonte | *"ingestão desta fonte"* |
| Ingestão de anotação | *"insight: [texto]"* |
| Estado de capítulo | *"como está o cap. X?"* |
| Estado de conceito | *"estado de [[conceitos/X]]"* |
| Lint completo | *"roda um lint"* |
| Lint focado | *"lint do cap. X"* / *"checa órfãos em autores/"* |
| Revisão crítica | *"revisa esse parágrafo como crítico sincero"* |
| Revisão gramatical | *"revisa gramática deste trecho"* |
| Draft de página | *"esboça a página de [autor X]"* |
| Conectar pontos | *"qual a relação entre X e Y na tese?"* |

---

## 11. Resolução de problemas

### Links internos não funcionam no Obsidian

**Sintoma:** links `[[conceitos/X]]` aparecem em vermelho ou não abrem.
**Causa:** o arquivo não existe ou o caminho está errado.
**Solução:**
1. Verifique se o arquivo existe em `wiki/conceitos/X.md`
2. Confira se o vault foi aberto na pasta correta (`writing-wiki/`, não `wiki/`)
3. Obsidian faz links relativos à raiz do vault — não inclua `wiki/` se a pasta raiz já é `writing-wiki/`

### O agente não encontra os arquivos

**Sintoma:** o agente diz que não consegue ler `CLAUDE.md` ou `wiki/index.md`.
**Causa:** a pasta do vault não está conectada ao Cowork.
**Solução:**
1. No Cowork, clique em "Select folder" e selecione novamente a pasta `writing-wiki/`
2. Confirme que a pasta aparece como conectada no painel do Cowork

### Git diz "not a git repository"

**Sintoma:** comandos Git retornam erro sobre não ser um repositório.
**Causa:** o `git init` não foi executado na pasta correta.
**Solução:**
```bash
# Navegue até a pasta raiz do vault
cd /caminho/para/writing-wiki
git init
git add .
git commit -m "setup inicial"
```

### Obsidian não mostra a pasta `wiki/` no painel lateral

**Sintoma:** o painel esquerdo mostra apenas `CLAUDE.md` e `MANUAL.md`, sem a pasta `wiki/`.
**Causa:** a pasta `wiki/` está vazia ou o Obsidian está filtrado.
**Solução:**
1. Verifique se os arquivos existem dentro de `wiki/`
2. Clique com o botão direito no painel lateral → "Reveal in file explorer" para confirmar

### O plugin Dataview não mostra resultados

**Sintoma:** blocos `dataview` aparecem em branco ou com erro.
**Causa:** o plugin pode não estar ativado ou a sintaxe está incorreta.
**Solução:**
1. Settings → Community Plugins → confirme que Dataview está ativado
2. Verifique se a sintaxe usa três crases e a palavra `dataview` logo após:
   ````
   ```dataview
   LIST FROM "wiki/autores"
   ```
   ````

---

## 12. Estrutura de arquivos explicada

```
writing-wiki/                    ← RAIZ DO VAULT (abrir esta pasta no Obsidian)
│
├── CLAUDE.md                    ← Configuração do agente de IA — PREENCHER PRIMEIRO
├── MANUAL.md                    ← Este arquivo
├── README.md                    ← Descrição do projeto (para GitHub)
├── .gitignore                   ← Arquivos que o Git deve ignorar
│
└── wiki/                        ← Todo o conteúdo da pesquisa fica aqui
    │
    ├── index.md                 ← MAPA DE TUDO — atualizar a cada novo arquivo
    ├── log.md                   ← Registro cronológico append-only
    │
    ├── tese/                    ← Arquivos do argumento e capítulos
    │   ├── argumento-central.md ← O arquivo mais importante — a tese em uma página
    │   ├── cap1-introducao.md   ← Capítulo 1: Introdução
    │   ├── cap2-[titulo].md     ← Capítulo 2 (renomear conforme o título)
    │   └── lacunas.md           ← Pontos em aberto e tensões não resolvidas
    │
    ├── autores/                 ← Uma página por autor mobilizado na tese
    │   ├── autor-01.md          ← Template — renomear para o sobrenome do autor
    │   └── autor-02.md          ← Copiar para quantos autores precisar
    │
    ├── conceitos/               ← Uma página por conceito-chave do argumento
    │   ├── conceito-01.md       ← Template — renomear para o nome do conceito
    │   └── conceito-02.md       ← Copiar para quantos conceitos precisar
    │
    └── tensoes/                 ← Uma página por tensão teórica identificada
        ├── tensao-01.md         ← Template — renomear para descrever o conflito
        └── tensao-02.md         ← Copiar para quantas tensões precisar
```

### Por que esta estrutura?

- **`tese/`** centraliza o argumento — é onde o pensamento acontece
- **`autores/`** separa o que é do autor do que é seu
- **`conceitos/`** força a definição operativa (o que o conceito faz *nesta tese*)
- **`tensoes/`** torna os conflitos explícitos em vez de implícitos
- **`index.md`** é o ponto de entrada para qualquer consulta — do agente ou sua
- **`log.md`** garante rastreabilidade de todas as mudanças

---

## Licença e créditos

Este template é distribuído sob licença MIT — use, modifique e redistribua livremente,
com ou sem atribuição.

Baseado em práticas de gestão de conhecimento para escrita acadêmica longa,
combinando conceitos de Zettelkasten, wiki pessoal e fluxos de trabalho com IA.

---

*Última atualização do manual: verifique o `log.md` do projeto.*
