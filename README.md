# EMA · RSI

Moyennes mobiles et RSI réunis dans **un seul indicateur** TradingView.

Il sert à repérer, en daily / weekly, le moment où un titre en tendance revient sur un support avec un RSI en survente.

![Aperçu](https://i.imgur.com/uBNe1xy.jpeg)

## Installation

1. Ouvrir l'**éditeur Pine Script** de [TradingView](https://tradingview.com/).
2. Coller le contenu de [`Main_Indicator.pine`](Main_Indicator.pine).
3. **Enregistrer**, puis **Ajouter au graphique**.
4. Retirer l'ancien indicateur de moyennes et le RSI natif.

## Comment le lire

| Repère | Où | Ce que ça veut dire |
|---|---|---|
| Point vert | RSI et sous la bougie | Le RSI repart de la survente, dans le sens de la tendance |
| **Gros point vert** | RSI et sous la bougie | Pareil, pendant que le prix touche la MA 100 ou l'EMA 200 : **le signal le plus solide** |
| Anneau vert | RSI et sous la bougie | Survente à contre-tendance : rebond possible, mais plus risqué |
| Point rouge | RSI et au-dessus de la bougie | Le RSI repart du surachat |
| Triangle vert ou rouge | RSI | Survente ou surachat **confirmé** (failure swing de Wilder) |
| Div+ / Div− | RSI | Divergence : le prix et le RSI ne vont plus dans le même sens |
| « RSI 30 à 76,40 » | À droite du prix | Une clôture à 76,40 ou moins ferait passer le RSI en survente |
| EMA 32, MA 100, EMA 200 | Prix | Tendance court terme et grands supports |

**Le tableau**, en haut à droite :

- **Tendance CT** : haussière ou baissière, et depuis combien de barres.
- **MA 100 / EMA 200** : écart du cours avec chaque support. Orange quand le prix est dessus.
- **RSI** : sa valeur, et depuis combien de barres il est en zone extrême.
- **Régime RSI** : haussier si le RSI tient au-dessus de 40, baissier s'il plafonne sous 60.

## Les alertes les plus utiles

Clic droit sur le graphique, **Ajouter une alerte**, condition **EMA · RSI**, fréquence **Une fois par clôture de barre**.

- **RSI se retourne en survente sur un support** : le gros point vert.
- **Failure swing haussier** : la survente confirmée.
- **RSI entre en survente** : pour être prévenu dès que le titre devient intéressant.

Dix autres alertes sont disponibles dans la même liste (surachat, divergences, contact d'un support…).

## Réglages à faire varier

Les réglages par défaut conviennent au daily et au weekly. À changer seulement si besoin :

| Réglage | Groupe | Quand |
|---|---|---|
| Thème | Apparence | Pour accorder les couleurs à ta chart (Actuel, Cobalt, Graphite, Nuit verte) |
| Seuils adaptatifs | 3 · RSI | Si le RSI du titre ne descend jamais à 30 |
| Masquer les points contre la tendance | 4 · Signaux du RSI | Pour ne garder que les signaux dans le sens de la tendance |
| Divergences en formation | 5 · Divergences du RSI | Pour les voir plus tôt, avec plus de fausses alertes |
| Tolérance de contact | 2 · Nuage et supports | À monter sur un titre très volatil |
| EMA 13 et nuage | 1 et 2 | À réafficher sur une chart weekly |
| Support 2 en SMMA 99 | 1 · Moyennes mobiles | Pour retrouver l'ancienne « EMA 200 » de la version précédente |

## Bon à savoir

- Les points, triangles et divergences sont confirmés à la clôture : ils ne bougent plus ensuite.
- Le niveau « RSI 30 à … » vaut pour la prochaine clôture et se recalcule à chaque bougie.
- Après une mise à jour du code, retire l'indicateur du graphique puis remets-le.
- C'est un outil de lecture, pas un conseil en investissement.
