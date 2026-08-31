# Sessão da Tarde

Estudo de dados sobre os filmes exibidos na **Sessão da Tarde**, da Globo. O projeto documenta a coleta, a limpeza e a análise exploratória de registros de exibição, enriquecidos com metadados do [The Movie Database](https://www.themoviedb.org/).

O conteúdo é publicado como um site Quarto: <https://erlonl.github.io/SessaodaTarde/>

## Percurso do estudo

1. [`scraping.ipynb`](sessao_da_tarde/scraping.ipynb) — coleta a listagem do [TV Globo Wiki](https://tvglobo.fandom.com/pt-br/wiki/Lista_de_filmes_exibidos_na_Sess%C3%A3o_da_Tarde).
2. [`cleaning.ipynb`](sessao_da_tarde/cleaning.ipynb) — remove registros sem filme e normaliza títulos.
3. [`Analysis.ipynb`](sessao_da_tarde/Analysis.ipynb) — explora recorrências, avaliações e a distância entre lançamento e exibição.

Os CSVs intermediários e finais permanecem em [`sessao_da_tarde/datasets`](sessao_da_tarde/datasets) para preservar a linhagem dos dados.

## Desenvolvimento local

O site usa os outputs salvos nos notebooks e, por padrão, não reexecuta código durante o build. Neste ambiente, use o Quarto com o Python de `~/.localvenv`:

```bash
QUARTO_PYTHON=~/.localvenv/bin/python quarto preview
```

Para gerar a versão estática:

```bash
QUARTO_PYTHON=~/.localvenv/bin/python quarto render
```

O resultado é escrito em `_site/`.

### Reexecutar os notebooks

As dependências estão registradas em `requirements.txt`. Para preparar o ambiente existente:

```bash
~/.localvenv/bin/python -m pip install -r requirements.txt
```

Execute os notebooks na ordem do estudo. A coleta depende da estrutura atual de uma página externa; para apenas atualizar a análise a partir dos CSVs versionados, reexecute `Analysis.ipynb` sem rodar o scraping.

## Publicação

O workflow [`.github/workflows/publish.yml`](.github/workflows/publish.yml) renderiza o projeto e publica o resultado na branch `gh-pages` a cada push em `main` ou por acionamento manual.

Na primeira publicação, confirme em **Settings → Pages** que a fonte está configurada como **Deploy from a branch**, usando `gh-pages` e a pasta `/ (root)`. Em **Settings → Actions → General**, o workflow precisa de permissão de leitura e escrita para criar ou atualizar essa branch.

## Escopo atual

A análise é exploratória e está em andamento. Perguntas sobre gênero, público-alvo e previsão de futuras exibições permanecem como trabalho futuro; o site não as apresenta como resultados concluídos.
