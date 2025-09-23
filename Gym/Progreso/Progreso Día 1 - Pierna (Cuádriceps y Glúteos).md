# Vista General
```dataview
TABLE Duración, rpe_session AS "RPE",
    max_bulgara + "kg x " + max_bulgara_reps AS "Búlgara",
    max_prensa + "kg x " + max_prensa_reps AS "Prensa",
    max_hip1 + "kg x " + max_hip1_reps AS "Hip Thrust (Máquina)",
    max_extensión + "kg x " + max_extensión_reps AS "Extensiones de Cuádriceps",
    max_femoral + "kg x" + max_femoral_reps AS "Curl Femoral (Sentado)",
    max_abducciones + "kg x" + max_abducciones_reps AS "Abducciones en Máquina",
    max_talonPie + "kg x" + max_talonPie_reps AS "Elevaciones de Talón Sentado"
FROM "Gym/Registros/Dia 1"
SORT date DESC
LIMIT 10
```
---
---
# Progreso en Ejercicios
## Sentadilla Búlgara
```tracker
searchType: frontmatter
searchTarget: max_bulgara
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Sentadilla Búlgara
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
---
---
## Prensa de Piernas
```tracker
searchType: frontmatter
searchTarget: max_prensa
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Prensa de Piernas
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
---
---
## Hip Thrust
```tracker
searchType: frontmatter
searchTarget: max_hip1
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Hip Thrust
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
---
---
## Extensión de Cuadriceps
```tracker
searchType: frontmatter
searchTarget: max_extensión
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Extensión de Cuádriceps
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
---
---
## Curl Femoral
```tracker
searchType: frontmatter
searchTarget: max_femoral
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Curl Femoral
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
---
---
## Abducciones en Máquina
```tracker
searchType: frontmatter
searchTarget: max_abducciones
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Abducciones
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
---
---
## Elevación de Gemelos
```tracker
searchType: frontmatter
searchTarget: max_talonPie
folder: Gym/Registros/Dia 1
line:
    title: Progreso en Elevación de Gemelos
    yAxisLabel: Peso (kg)
    xAxisLabel: Fecha
    yAxisUnit: kg
```
