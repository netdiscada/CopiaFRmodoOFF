# FR Offline (CopiaFRmodoOFF)

Versão do app **FR — Relatório Diário (SMSUZ)** que **não usa servidor**: sem Firebase, sem login, sem ADM/chefe.
Um funcionário só, dados guardados no próprio celular (IndexedDB), backup por arquivo `.json`.
É uma cópia do `netdiscada/fr-apk` com a camada de dados trocada — o resto (telas, PDF, km, inspeção) é o mesmo.

## Leia nesta ordem

1. `AGENTS.md` — regras de como trabalhar neste projeto (português, km sempre digitado, provar antes de commitar).
   Atenção: o trecho "A versão atual está descartada" é de 28/10 e ficou **velho** — o app foi refeito depois
   (ver `PLANO.md`). O que continua valendo: a fonte do código é o `fr-apk`, nunca a pasta `fr/` do PC-DO-HERMES.
2. `PLANO.md` — o que já foi feito, passo a passo, e o que falta (cadastro de veículos testado no navegador,
   teste completo entrar → cadastrar veículo → começar dia → encerrar → PDF).
3. `fotos-passo3/` … `fotos-passo7/` — fotos das provas de cada passo (só consulta).

## Estrutura

Diferente do `fr-apk`, **não existe `www/`**: o app está direto na raiz.

```
index.html, css/, js/, vendor/, fonts/, icons/, assets/   o app (HTML/CSS/JS puro, sem build)
js/db.js              camada de dados em IndexedDB (mesmos nomes de função do db.js do fr-apk)
js/backup-offline.js  exportar/importar o backup .json
sw.js, manifest.json  versão site instalável (PWA), abre sem internet
android/              projeto Capacitor 8
testes/               testes (copiados do fr-apk; ver testes/LEIAME.md — alguns casos, como adm/chefe,
                      são do fr-apk e podem não se aplicar aqui)
```

## Publicação

Este repositório **não tem workflows** (`.github/` não existe): nada é publicado sozinho a partir daqui.
O `PLANO.md` cita o site `https://netdiscada.github.io/fr-offline/`, que não é deste repositório — confirmar
com o usuário onde ele é publicado antes de prometer qualquer lançamento.

## Regras para continuar

- Mudança no comportamento do FR vem **primeiro do `fr-apk`** (fonte); aqui só se adapta o que depende de servidor.
- Para trazer novidades do `fr-apk`, use a skill `portar-projeto` (fica em `PC-DO-HERMES/.claude/skills/`).
- Não mexer no `fr-apk` nem no `fr-releases` a partir deste projeto: os celulares dos funcionários dependem deles.

## Branches

- `main` — versão atual (a última obra é "Editar perfil + aviso sem veículos").
- `ccr-783cc9bb-tbu1iq` — 2 commits de reescrita do `AGENTS.md` que **não entraram no `main`**. Conferir antes de apagar.
