# qa_examen_automatizacion_pruebas

Proyecto Java (Maven + JUnit 5) para automatizacion de pruebas y CI con Jenkins.  
Incluye pipeline declarativo que compila, ejecuta tests y publica resultados JUnit y artefactos del target/

## Requisitos

- Java 17
- Maven 3.9
- Git
- Jenkins (en local o servidor) con:
  - Plugins: Pipeline, Git, JUnit
  - Herramienta Maven registrada como M3  
    (Manage Jenkins -> Tools -> Maven installations -> Name: M3 -> Install automatically)

## Estructura

qa_examen_automatizacion_pruebas/
|- pom.xml
|- Jenkinsfile
|- README.md
L src
   L test
      L java
         L cl
            L qa_examen
               L EjercicioUnitTest.java

## Ejecutar local (CMD/PowerShell)

mvn clean test

Reportes JUnit: target/surefire-reports/*.xml

## 4 Estrategia ramas

main: rama estable
feature/ : ramas cortas (feature/ci-pipeline)

git checkout -b feature/ci-pipeline
git add .
git commit -m "feat(ci): Jenkinsfile + tests"
git push -u origin feature/ci-pipeline

## Pipeline Jenkins (Pipeline SCM)

Nueva tarea -> Pipeline -> nombre: qa_examen_automatizacion_pruebas

Definition: Pipeline script from SCM
SCM: Git
Repository URL: https://github.com/motola720/qa_examen_automatizacion_pruebas.git
Branches to build: */feature/ci-pipeline
Script Path: Jenkinsfile



