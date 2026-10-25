# Casa da Nota

Quiz do braço do violão, para os alunos do Sidney (SESI-SP). Um único arquivo HTML (`index.html`), publicado pelo GitHub Pages. Responda e escreva comentários em **português do Brasil**.

- Site: `https://rapososidney.github.io/casa-da-nota/`
- Publicar = `git push` na `main`. O Pages leva 1–2 min, e o navegador pode manter respostas em cache por até 10 min (para conferir antes disso, use `?v=N` na URL).
- Faça commit só quando o Sidney pedir. Mensagens de commit em português.
- Este arquivo veio de `casa-da-nota-3.html` no repositório antigo `Quizes-Musicais-Teste` (em aposentadoria). As regras comuns a todos os projetos estão no `CLAUDE.md` da pasta `Documentos\GitHub`.
- **Sem `manifest`/`sw.js`**: o arquivo de origem nunca foi instalável, então a migração manteve assim. Se o Sidney quiser o app instalável, adicionar seguindo o padrão do [`afinador`](https://rapososidney.github.io/afinador/) (prefixo `casaDaNota-` no cache).

## Regras do repositório

- **Tudo no `index.html`, sem dependências externas**: sem CDN, sem build. Tem que abrir offline.
- `localStorage['casaDaNota_tema']` guarda só o tema claro/escuro. **A chave era genérica (`"tema-quiz"`) no arquivo de origem** — foi trocada por esse prefixo na migração porque a origem `rapososidney.github.io` é compartilhada com os outros quizzes do Sidney, e uma chave genérica faria um quiz mudar o tema de outro. Nunca volte a uma chave sem prefixo.

## O app (index.html)

Pergunta a casa (0–11, ajustável por `limiteRange`) onde uma nota (cifra ou nome, sorteado entre as grafias equivalentes — `C#`/`Db` etc.) aparece numa corda do violão, dada a pitch class da corda solta (`SOLTAS`, C=0). O aluno escolhe a corda (clicando nela) ou ativa "aleatória" (`modoAleatorio`, sorteia a corda a cada pergunta); nunca repete a mesma nota (pitch class) duas vezes seguidas (`ultimaPc`).

- Tempo-limite opcional por resposta (`tempoRange`, 0 = sem limite): barra decrescente (`elTempoFluxo`, transição CSS); se esgotar, conta como erro e mostra a resposta certa.
- Placar: acertos/total e sequência de acertos seguidos (zera a cada erro ou tempo esgotado).
- Tema claro/escuro com persistência em `localStorage` (ver acima).
