# EMA · RSI

Indicateur TradingView (Pine Script v6) qui réunit des moyennes mobiles sur le prix et un RSI dans **un seul indicateur**. 
Il n'occupe qu'une place sur le plan gratuit de TradingView.

Pensé pour le daily et le weekly : Repérer la tendance, les grands supports, et les extrêmes du RSI avec le moins de retard possible.

[Aperçu](https://i.imgur.com/nXQhP9h.jpeg)

## Installation

1. Ouvrir [TradingView](https://tradingview.com/) puis l'**éditeur Pine Script**.
2. Coller le contenu de [`Main_Indicator.pine`](Main_Indicator.pine).
3. Cliquer sur **Enregistrer**, puis **Ajouter au graphique**.
4. Retirer l'ancien indicateur de moyennes et le RSI natif, qui font doublon.

Après une mise à jour du code, retire l'indicateur du graphique puis remets-le, pour repartir des nouveaux réglages par défaut.

## Ce qu'il affiche

**Sur le prix**

- EMA 32, MA 100 et EMA 200. Les EMA 13 et 25, la MA 300 et une moyenne d'une autre unité de temps sont disponibles en option.
- Une moyenne n'apparaît qu'une fois qu'elle a assez d'historique (200 barres pour l'EMA 200).
- Les prix déclencheurs : la clôture qui ferait passer le RSI à 30 ou à 70 à la prochaine barre.
- Un tableau : tendance court terme, écart à la MA 100 et à l'EMA 200, RSI et durée en zone extrême, régime du RSI.

**Dans le volet RSI**

- Les points de retournement en zone extrême, une barre après le creux ou le sommet :

  | Point | Signification |
  |---|---|
  | Plein | Dans le sens de la tendance de fond (cours au-dessus de l'EMA 200 pour une survente) |
  | Gros et plein | Survente pendant que le prix touche la MA 100 ou l'EMA 200 |
  | Anneau | Contre la tendance de fond |

- Les failure swings de Wilder (triangles), qui confirment une survente ou un surachat.
- Les divergences, filtrées pour ne garder que celles qui partent d'une zone extrême.
- Une bande entre les seuils, fixes (30 / 70) ou adaptatifs au titre.

**Thèmes** : Actuel, Cobalt, Graphite et Nuit verte, au choix dans le groupe Apparence.

## Réglages utiles

Les réglages par défaut conviennent pour commencer. Ceux qui valent la peine d'être changés :

| Réglage | Groupe | Quand le changer |
|---|---|---|
| Thème | Apparence | Pour l'accorder aux couleurs de ta chart |
| Seuils adaptatifs | 3 · RSI | Titre en forte tendance, dont le RSI ne descend jamais à 30 |
| Longueur 9 au lieu de 14 | 3 · RSI | Pour un RSI plus réactif, avec davantage de signaux |
| Masquer les points contre la tendance | 4 · Signaux du RSI | Pour ne garder que les signaux dans le sens de la tendance |
| Divergences en formation | 5 · Divergences du RSI | Pour les voir plus tôt, avec quelques fausses alertes |
| Tolérance de contact | 2 · Nuage et supports | À monter sur un titre très volatil, à baisser pour des contacts plus stricts |
| EMA 13 et nuage | 1 et 2 | À réafficher sur une chart weekly |
| Support 2 en SMMA 99 | 1 · Moyennes mobiles | Pour retrouver l'ancienne « EMA 200 » (une SMMA 99 équivaut à une EMA 197) |

## Alertes

Clic droit sur le graphique, **Ajouter une alerte**, condition **EMA · RSI**. Choisir la fréquence **Une fois par clôture de barre**.

- RSI entre en survente / en surachat
- RSI se retourne en survente / en surachat
- RSI se retourne en survente sur un support
- Failure swing haussier / baissier
- Divergence haussière / baissière
- Contact d'un support
- Croisement haussier / baissier court terme
- Clôture sous le Support 2

## Bon à savoir

- Les prix déclencheurs valent pour la **clôture** de la prochaine barre, et se recalculent à chaque nouvelle bougie. Le calcul est celui du RSI inversé de Giorgos Siligardos.
- Les points, triangles et divergences sont confirmés à la clôture de la barre : ils ne changent pas après coup. Seules les divergences en formation, en option, sont provisoires par nature.
- TradingView garde au maximum 500 étiquettes par indicateur. Sur un très long historique, les points et divergences les plus anciens disparaissent.
- Un outil de lecture, pas un conseil en investissement.
