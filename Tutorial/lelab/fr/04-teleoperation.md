[English](../en/04-teleoperation.md) | [简体中文](../zh-hans/04-teleoperation.md) | [繁體中文](../zh-hant/04-teleoperation.md) | [Deutsch](../de/04-teleoperation.md) | [Español](../es/04-teleoperation.md) | Français | [Italiano](../it/04-teleoperation.md) | [日本語](../ja/04-teleoperation.md) | [한국어](../ko/04-teleoperation.md) | [Português (BR)](../pt-br/04-teleoperation.md) | [Português (PT)](../pt-pt/04-teleoperation.md)

# 4 · Téléopération

> **Précédent :** [03 Connexion et calibration](03-calibration.md)
> **Suivant :** [05 Enregistrer un jeu de données](05-record-dataset.md)

Vous déplacez le bras leader à la main ; le follower copie le mouvement. C'est ainsi que vous enregistrez des démonstrations, et le moyen le plus rapide de confirmer la calibration.

## Le lancer

1. Ouvrez l'onglet **Teleoperation**.
2. Confirmez les ports et le profil de calibration — LeLab se souvient de ceux de la calibration.
3. Lancez la téléopération.
4. Déplacez le bras leader.

L'onglet diffuse les positions des articulations pendant l'exécution. Appuyez sur stop une fois terminé.

**C'est Stop qui met le follower au repos.** Fermer l'onglet ou tuer le processus laisse le bras là où il est.

## Ce qu'il faut vérifier

| Vérification | Pourquoi |
|---|---|
| Le follower suit sans à-coups, sans retard ni tremblement | Un suivi approximatif donne des données d'entraînement inutilisables |
| La plage du follower correspond à celle du leader | S'arrêter court ou buter sur une limite signifie qu'une articulation est mal calibrée — revenez à la [page 3](03-calibration.md) |
| Les deux bras bougent dans le même sens | Un follower inversé signifie qu'une articulation a été calibrée dans le mauvais sens |
| Rien n'entre en collision aux extrémités | Parcourez toute la plage que vous prévoyez d'utiliser |

Si le mouvement est incorrect sans être cassé — décalage, une articulation inversée, plage incomplète — recalibrez plutôt que de compenser. Un bras mal calibré produit un jeu de données qui entraîne la policy à faire la mauvaise chose.

## Caméras

Si des caméras sont configurées, la vue de téléopération montre leurs aperçus.

- Caméra de poignet : montre-t-elle la pince et ce qu'elle s'apprête à saisir ?
- Caméra fixe : montre-t-elle tout l'espace de travail ?
- L'une des deux images est-elle sur le côté ou à l'envers ? Corrigez la **rotation** dans l'[onglet Calibration](03-calibration.md) avant d'enregistrer.

Les images enregistrées pendant la téléopération sont la seule chose que la policy verra jamais.

---

> **Suivant :** [05 Enregistrer un jeu de données](05-record-dataset.md)
