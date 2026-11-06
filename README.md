# Microgrid PV–batterie d'une maison à Casablanca

Page en ligne : https://ritarochd-jpg.github.io/microgrid-site/

J'ai dimensionné, modélisé et commandé sous MATLAB/Simulink le microgrid d'une maison individuelle à Casablanca : champ photovoltaïque, batterie, onduleur raccordé au réseau et groupe électrogène de secours. Cette page présente le système à deux échelles de temps.

## Contenu de la page

1. **La journée, minute par minute.** Simulateur énergétique au pas d'une minute avec les règles de mon superviseur (EMS). On peut couper le réseau, faire passer un nuage ou ajouter une charge, et suivre la réponse du système.
2. **La demi-seconde, à l'échelle des convertisseurs.** Signaux exportés de ma simulation Simulink du système complet, commandes en boucle fermée.
3. **Méthode et limites.** Ce qui est validé en simulation électrique, ce qui est validé au niveau énergétique, et ce qui reste à faire.

## Le système

| Élément | Caractéristiques |
|---|---|
| Champ PV | 2 × 8 modules, 3,6 kWc |
| Batterie | LFP 32 S, 102,4 V, 100 Ah (10,24 kWh), SOC maintenu entre 20 et 90 % |
| Bus continu | 400 V |
| Onduleur | monophasé 4 kVA, 230 V, 50 Hz |
| Groupe de secours | 2 kW |
| Consommation | 10,7 kWh/jour |

## Commandes réalisées sous Simulink

- MPPT par perturbation et observation sur le hacheur boost
- Boucles de courant et de tension réglées par placement de pôles
- Boucle de courant du convertisseur batterie
- PLL SOGI et correcteur proportionnel-résonant pour l'onduleur
- Régulation de la tension du bus continu
- Statisme et régulation de tension du groupe électrogène
- Superviseur à règles : gestion du SOC, hystérésis du groupe, délestage

## Principaux résultats (mode raccordé, 1000 W/m², charge 1 kW)

- 3,70 kW extraits par le MPPT en 0,15 s
- Bus continu tenu à 400 V ± 0,6 V en régime établi
- Courant de l'onduleur en phase avec le réseau (déphasage d'environ 2°)

## Limites

Les modes îlotage et secours sont validés au niveau énergétique seulement. Les pertes des convertisseurs, l'effet de la température et les protections ne sont pas encore modélisés. Le courant de l'onduleur présente une ondulation haute fréquence qui reste à éliminer.

## Données

Production de décembre : moyenne horaire PVGIS à Casablanca (33,57° N). Courbes Simulink : export des scopes du modèle complet.

## Fichiers

- `index.html` : la page et le simulateur
- `simulink_data.js` : signaux exportés de la simulation Simulink

## Contact

Rita Rochd, élève ingénieure en génie électrique (électrotechnique et électronique de puissance)
ritarochd@gmail.com · [LinkedIn](https://www.linkedin.com/in/rita-rochd)
