# Vista General
```dataview
TABLE Duración, rpe_session AS "RPE",
    max_pressInclinado + "kg x " + max_pressInclinado_reps AS "Press Inclinado con Mancuernas",
    max_remoM + "kg x " + max_remoM AS "Remo con Mancuernas",
    max_militar + "kg x " + max_militar AS "Press de Hombros",
    max_jalonNeutro + "kg x " + max_jalonNeutro_reps AS "Jalón al Pecho (Agarre Neutro)",
    max_lats + "kg x " + max_lats AS "Elevaciones Laterales",
    max_triceps + "kg x " + max_triceps AS "Extensiones de Tríceps en Polea Alta"   
FROM "Gym/Registros/Dia 2"
SORT date DESC
LIMIT 10
```
```tracker
searchType: frontmatter
searchTarget: max_pressInclinado
folder: Gym/Registros/Dia 2
line:
    title: Progreso en Press Inclinado con Mancuernas
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_remoM
folder: Gym/Registros/Dia 2
line:
    title: Progreso en Remo con Mancuernas
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_militar
folder: Gym/Registros/Dia 2
line:
    title: Progreso en Press de Hombro
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_jalonNeutro
folder: Gym/Registros/Dia 2
line:
    title: Progreso en Jalón al Pecho
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_lats
folder: Gym/Registros/Dia 2
line:
    title: Progreso en Elevaciones Laterales
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
```tracker
searchType: frontmatter
searchTarget: max_triceps
folder: Gym/Registros/Dia 2
line:
    title: Progreso en Extensión de Tríceps
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
