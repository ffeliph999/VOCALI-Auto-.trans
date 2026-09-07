# VOCALI — Vocaloid Auto Trans

Gerador automático de arquivos `.trans` (transcrição) para bancos de voz Vocaloid de 3º geração, a partir dos nomes dos arquivos `.wav`.

Criado por **Felipe Souza (Otomi Kazuo)**.

## O que faz

Lê todos os arquivos `.wav` da pasta onde está o executável, separa os tokens fonéticos do nome do arquivo (separados por `_`), aplica a divisão silábica (CVVC, VCV ou Híbrido) e as substituições fonéticas necessárias (SAMPA), e gera um arquivo `.trans` correspondente para cada `.wav`.

## Como usar

1. Coloque o `VOCALI.exe` na mesma pasta dos arquivos `.wav` que você quer processar.
2. Dê duplo clique no `VOCALI.exe` (abre um terminal).
3. Escolha o tipo de banco:
   - `1` — CVVC
   - `2` — VCV
   - `3` — Híbrido (CVVC + VCV)
4. Responda se deseja remover a última janela que termina em `Sil` (padrão: Sim).
5. Aguarde o processamento — uma barra de progresso mostra o andamento.
6. Ao final, um arquivo `.trans` é gerado para cada `.wav`, na mesma pasta.

Pressione ENTER para fechar o programa quando terminar.

## Regras de nomenclatura dos arquivos

- Tokens separados por `_` (ex: `ka_sa`, `n_de`).
- Um token `n` isolado é tratado como a nasal silábica `N\`.
- Se o nome do arquivo contiver `j`, todo `j` interno é convertido para `dZ`.

## Modos de banco

- **CVVC**: divide cada token em prefixo consonantal + vogal (+ sufixo), gerando pares consecutivos `[X Y]`.
- **VCV**: agrupa em clusters conhecidos (`ky`, `sh`, `ts`, etc.) e gera trios `[V C V]` ou pares `[V V]`.
- **Híbrido**: combina pares consecutivos (CVVC) com trios VCV quando aplicável.

## Substituições fonéticas aplicadas

| Original | Vira |
|---|---|
| `hy` | `C` |
| `ny` | `J` |
| `ry` | `4'` |
| `fy` | `p\'` |
| `sh` | `S` |
| `ch` | `tS` |
| `f` | `p\` |
| `u` | `M` |
| `r` | `4` |
| `y` | `j` ou `'` (conforme contexto) |

## Requisitos

Nenhum — o `.exe` já inclui tudo, não precisa de Python instalado.
