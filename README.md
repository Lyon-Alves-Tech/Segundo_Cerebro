# writing-wiki

**Segundo cérebro para pesquisa acadêmica de escrita longa.**

Um template de vault Obsidian estruturado para teses, dissertações e livros — com integração a agentes de IA (Claude/Cowork) e versionamento via Git.

---

## O que este template oferece

- **Estrutura wiki** com arquivos organizados por função: autores, conceitos, tensões, capítulos
- **Argumento central** como página-âncora de toda a pesquisa
- **Rastreamento de lacunas** — pontos em aberto e tensões teóricas não resolvidas
- **Log cronológico** de todas as operações na wiki
- **Integração com agente de IA** via `CLAUDE.md` (Claude/Cowork)
- **Git pronto** com `.gitignore` configurado para vault Obsidian

---

## Início rápido

```bash
# 1. Clone o repositório
git clone https://github.com/SEU-USUARIO/writing-wiki.git

# 2. Abra a pasta writing-wiki/ como vault no Obsidian
#    File → Open folder as vault → selecione writing-wiki/

# 3. Preencha CLAUDE.md com os dados do seu projeto

# 4. Comece pela página mais importante:
#    wiki/tese/argumento-central.md
```

Para instruções detalhadas, leia o **[MANUAL.md](MANUAL.md)**.

---

## Estrutura

```
writing-wiki/
├── CLAUDE.md              ← configuração do agente de IA
├── MANUAL.md              ← instalação e uso detalhados
└── wiki/
    ├── index.md           ← mapa de tudo
    ├── log.md             ← histórico de operações
    ├── tese/
    │   ├── argumento-central.md
    │   ├── cap1-introducao.md
    │   ├── cap2-primeiro-capitulo.md
    │   └── lacunas.md
    ├── autores/           ← uma página por autor mobilizado
    ├── conceitos/         ← uma página por conceito-chave
    └── tensoes/           ← uma página por tensão teórica
```

---

## Para quem é este template

- Pesquisadores de pós-graduação (mestrado, doutorado)
- Autores de livros acadêmicos ou de não-ficção densa
- Qualquer pessoa que escreve textos longos com muitas referências e um argumento central

---

## Requisitos

- [Obsidian](https://obsidian.md) (gratuito)
- [Git](https://git-scm.com) (para versionamento)
- [Claude/Cowork](https://claude.ai) (opcional — para uso com agente de IA)

---

## Licença

MIT — use, modifique e redistribua livremente.
