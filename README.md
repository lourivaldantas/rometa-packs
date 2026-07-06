# rometa-packs 🎁

Repositório comunitário de **pacotes de prêmios** do
[Rometa](https://github.com/lourivaldantas) — o app de rotina e
gamificação. Cada pacote é um JSON puro com recompensas condicionais
("bati X% das metas do período → libero o prêmio") prontas para
instalar na galeria do app.

## Como usar

O app Rometa lê o [`index.json`](index.json) deste repositório e mostra
os pacotes na galeria da aba **Prêmios** (ícone de lojinha). É só tocar
em **Instalar**.

## Como contribuir com um pacote

1. Faça um fork deste repositório.
2. Crie `packs/<id-do-seu-pacote>.json` seguindo o formato abaixo.
3. Adicione o conteúdo do pacote ao array `packs` do `index.json`.
4. Abra um pull request — a revisão do PR é a moderação da comunidade.

## Formato (`rometa-reward-pack` v1)

```json
{
  "format": "rometa-reward-pack",
  "version": 1,
  "id": "meu-pacote",
  "name": "Meu pacote",
  "author": "@seunome",
  "description": "Uma frase vendendo o pacote.",
  "icon": "gift-outline",
  "rewards": [
    {
      "title": "Assistir 2 episódios de dorama",
      "description": "Sessão dupla no fim de semana.",
      "scope": "weekly",
      "threshold": 90,
      "unlockDay": 6,
      "icon": "drama-masks"
    }
  ]
}
```

| Campo do prêmio | Valores | Obrigatório |
|---|---|---|
| `title` | texto | sim |
| `description` | texto | não |
| `scope` | `weekly` \| `biweekly` \| `monthly` | sim |
| `threshold` | 1–100 (% das metas do período) | sim |
| `unlockDay` | 0 (domingo) … 6 (sábado), ou `null` | não |
| `icon` | nome de ícone [MaterialCommunityIcons](https://icons.expo.fyi/) | não |

Dica: no app, **Exportar meus prêmios** copia o JSON dos seus prêmios
já no formato certo — é o jeito mais fácil de começar um pacote.

Pacotes são só dados (sem código). O app valida cada campo e ignora
pacotes malformados; ícones inexistentes viram um presente 🎁.
