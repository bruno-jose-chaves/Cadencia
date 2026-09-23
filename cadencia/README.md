# CADÊNCIA

Cronômetro de tiro e registro de treino para IPSC/IDPA.
App single-file em HTML + JavaScript puro, sem build step.

Site: https://cadencia-cronometro-registro.netlify.app

## Estrutura

| Pasta | Função |
|---|---|
| `public/` | O que vai para o ar. A Netlify publica só esta pasta. |
| `versoes/` | Arquivo histórico. Versionado no Git, **não** publicado. |

## Deploy

Automático. Todo push na branch `main` dispara um deploy na Netlify.

- Build command: nenhum (o app não compila nada)
- Publish directory: `public`
- Configuração fixada em `netlify.toml`, que tem prioridade sobre o painel

Deploy manual por arrastar pasta (Netlify Drop) **não deve mais ser usado** —
foi o que apagou o `index.html` do site em 23/09/2026.

## Histórico de versões

| Versão | Observação |
|---|---|
| v1 – v4 | Evolução inicial do detector e da interface |
| v5 | **Não existe.** Ramo RMS+suppressor, construído sobre base errada e descartado. |
| v6 – v7 | Linha de produção com detector adaptativo de transiente |
| v8 | Biblioteca de drills, modo bloco, multiplayer Firebase |
| v9 | Redesign completo, responsividade e medição do microfone |

## Regras do projeto

- **Detector congelado.** `isShot`, `effThresh` e `updateFloor` não mudam a
  partir da v7, para preservar a calibração de campo. Alterar só com
  liberação explícita.
- **Arquivo único.** O app é um HTML só. Restrição inegociável.
- **Firebase.** A config é pública por design; a segurança fica nas regras do
  Firestore.
- **localStorage.** Chave `cadencia_v1`. Todas as versões leem e gravam o mesmo
  formato — trocar de versão não migra nem apaga dados.


## Pendências conhecidas

- Microfone ainda capta tiros das baias vizinhas. A janela anti-eco resolveu a
  contagem dupla do próprio disparo, mas filtrar o vizinho segue em aberto.
- Firebase Storage adiado por custo.
