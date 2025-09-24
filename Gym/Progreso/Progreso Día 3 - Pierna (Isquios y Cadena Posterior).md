```dataview
TABLE Duración, rpe_session AS "RPE",
    max_rdl + "kg x " + max_rdl_reps AS "Peso Muerto Rumano",
    max_sentadilla + "kg x " + max_sentadilla_reps AS "Sentadilla Hack",
    max_hip2 + "kg x " + max_hip2_reps AS "Hip Thrust (Unilateral)",
    max_bulgara + "kg x " + max_bulgara_reps AS "Sentadilla Búlgara",
    max_talonSentado + "kg x " + max_talonSentado_reps AS "Elevaciones de Talón (Sentado)"
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
