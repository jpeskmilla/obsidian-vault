```dataview
TABLE Duración, rpe_session AS "RPE",
    max_pressPlano + "kg x " + max_pressPlano_reps AS "Press de Banca con Mancuernas",
    max_remoPendlay + "kg x " + max_remoPendlay_reps AS "Remo Pendlay",
    max_fondos + "kg x " + max_fondos_reps AS "Fondos",
    max_jalonAmplio + "kg x " + max_jalonAmplio_reps AS "Jalón al Pecho (Agarre Amplio)",
    max_bicepsInclinado + "kg x " + max_bicepsInclinado_reps AS "Curl de Bíceps en Banco Inclinado",
    max_facePull + "kg x " + max_facePull_reps AS "Face Pull",
    max_pecDeck + "kg x " + max_pecDeck_reps AS "Pec Deck"
FROM "Gym/Registros/Dia 3"
SORT date DESC
LIMIT 10
```
```tracker
searchType: frontmatter
searchTarget: max_rdl
folder: Gym/Registros/Dia 3
line:
    title: Peso Muerto Rumano
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_sentadilla
folder: Gym/Registros/Dia 3
line:
    title: Sentadilla Hack
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_hip2
folder: Gym/Registros/Dia 3
line:
    title: Hipt Thrust (Unilateral)
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_bulgara
folder: Gym/Registros/Dia 3
line:
    title: Sentadilla Búlgara
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_talonSentado
folder: Gym/Registros/Dia 3
line:
    title: Elevaciones de Talon (Sentado)
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
