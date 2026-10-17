# Taller: matriz inicial de riesgos de sistemas

**Integrante:** Samuel Muriel Meneses  
**Asignatura:** Auditoría de Sistemas (ET0114)  
**Docente:** Juan Duque

## 1. Continuidad del caso

Este trabajo continúa el caso de **Bancolombia S.A.** desarrollado en el primer taller. Se conservan como criterios principales **COBIT 2019**, **ISO/IEC 27001:2022** e **ITIL 4**. El análisis se concentra en los canales digitales del banco y no pretende evaluar toda la organización.

## 2. Contexto actualizado

Bancolombia presta servicios financieros mediante canales como Mi Bancolombia, Sucursal Virtual Personas y Sucursal Virtual Negocios. En 2025, estos canales fueron usados mensualmente por 9,4 millones de clientes y procesaron más de 250 millones de transacciones monetarias, equivalentes al 98 % de este tipo de operaciones del banco. El proceso analizado comprende autenticación, transacciones, accesos privilegiados, monitoreo, continuidad y cambios de los canales digitales. Debido a su volumen y criticidad, una falla podría producir fraude, exposición de datos, alteración de transacciones o indisponibilidad del servicio. ([Bancolombia, 2026, pp. 108, 157 y 164–165](https://www.grupocibest.com/wcm/connect/bf5091ab-dd4e-44fd-9d43-7db2eb451f57/Bancolombia_Informe_de_Gestion_2025.pdf?MOD=AJPERES))

## 3. Activos y procesos considerados

| ID | Activo o proceso | Razón de criticidad |
|---|---|---|
| A-01 | Autenticación y autorización de transacciones digitales | Evita la suplantación y las operaciones no autorizadas. |
| A-02 | Datos personales, financieros y cuentas privilegiadas | Su exposición o alteración afectaría a clientes, al banco y al cumplimiento normativo. |
| A-03 | Registros de eventos y monitoreo de seguridad | Permiten detectar, investigar y responder a fraude e incidentes tecnológicos. |
| A-04 | Infraestructura, respaldos y recuperación de los canales digitales | Sostienen la disponibilidad y la recuperación íntegra del servicio. |
| A-05 | Proceso de cambios y liberaciones de software | Una modificación defectuosa o no autorizada puede afectar seguridad, datos y disponibilidad. |

## 4. Supuestos y limitaciones

- El análisis utiliza información pública de Bancolombia y lo definido en el primer taller; no se tuvo acceso a configuraciones, registros, contratos ni expedientes internos.
- La mención de un control en el informe público no demuestra por sí sola que esté bien diseñado ni que opere eficazmente. Esa validación queda como **evidencia por obtener**.
- Las vulnerabilidades se plantean como debilidades posibles que deben comprobarse; no constituyen hallazgos contra Bancolombia.
- Los valores corresponden a **riesgo inherente preliminar**, antes de validar la eficacia de los controles. El riesgo residual solo podrá calcularse después de las pruebas.
- Cualquier prueba técnica sobre sistemas reales requeriría autorización formal, alcance aprobado y reglas de trabajo.
- Como criterios legales se consideran la Ley 1581 de 2012 y la Ley 1273 de 2009. Para el sector financiero debe verificarse, antes de iniciar la auditoría, la versión consolidada vigente de las instrucciones de la Superintendencia Financiera sobre seguridad de la información y ciberseguridad.

## 5. Criterio de valoración

La probabilidad y el impacto se califican de 1 a 5, según la escala suministrada en el taller. El nivel se obtiene mediante `probabilidad × impacto`. Para ordenar la atención se usa esta interpretación: **crítico: 20–25; alto: 15–19; medio: 8–14; bajo: 1–7**. Esta clasificación es un criterio adoptado para el ejercicio y no una escala oficial atribuida a Bancolombia.

## 6. Matriz inicial de riesgos

| ID | Activo o proceso | Amenaza | Vulnerabilidad | Riesgo | P | I | Nivel | Control actual o evidencia | Control propuesto | Justificación |
|---|---|---|---|---|---:|---:|---:|---|---|---|
| R-01 | A-01. Autenticación y transacciones | Delincuentes que obtienen credenciales mediante suplantación, ingeniería social o malware | Posible cobertura desigual de autenticación reforzada, identificación del dispositivo o monitoreo basado en riesgo. **Supuesto por validar.** | Un tercero podría tomar una cuenta y ejecutar transacciones no autorizadas, causando pérdidas, reclamaciones y afectación reputacional. | 5 | 5 | **25 – Crítico** | El informe público menciona biometría facial y monitoreo analítico en tiempo real; su cobertura y eficacia son **evidencia por obtener**. | Autenticación multifactor (MFA) adaptativa, vinculación segura del dispositivo, monitoreo en tiempo real, alertas, bloqueo oportuno y revisión mensual de reglas antifraude. | El informe de 2025 atribuye 83 % de las pérdidas operacionales a fraude externo; el volumen digital amplía la exposición. |
| R-02 | A-02. Datos y cuentas privilegiadas | Colaborador, excolaborador, contratista o atacante con una cuenta privilegiada | Posibles cuentas huérfanas, privilegios excesivos, recertificaciones incompletas o insuficiente segregación. **Supuesto por validar.** | Una cuenta privilegiada podría usarse para consultar, extraer o modificar información y configuraciones sin autorización. | 4 | 5 | **20 – Crítico** | El banco declara un SGSI; inventarios de cuentas, revisiones de privilegios y bajas son **evidencia por obtener**. | Integrar altas, cambios y bajas con RR. HH.; gestión de accesos privilegiados (PAM), MFA, privilegios temporales, revisión trimestral y registro de sesiones. | Una sola cuenta con privilegios amplios podría producir un efecto material, aunque la debilidad aún debe comprobarse. |
| R-03 | A-03. Logs y monitoreo | Atacante externo o usuario interno que actúe sin detección oportuna | Posibles brechas de cobertura, correlación insuficiente, alertas no probadas o retención inadecuada. **Supuesto por validar.** | Un incidente podría permanecer sin detectar, ampliar su alcance e impedir una investigación completa. | 4 | 4 | **16 – Alto** | El informe menciona monitoreo preventivo y analítica; cobertura del SIEM, casos de uso y atención de alertas son **evidencia por obtener**. | Centralizar y proteger logs, sincronizar la hora, definir retención, monitorear continuamente y probar trimestralmente alertas y respuesta. | Los controles preventivos pueden fallar; detectar y contener constituye una segunda barrera indispensable. |
| R-04 | A-04. Infraestructura, respaldos y recuperación | Falla tecnológica, error, ciberataque, pérdida de conectividad o interrupción de un proveedor | Posibles dependencias sin redundancia o pruebas que no demuestren el tiempo y punto objetivo de recuperación (RTO/RPO). **Supuesto por validar.** | Los canales podrían quedar indisponibles o recuperar información incompleta, impidiendo transacciones. | 3 | 5 | **15 – Alto** | El banco informa disponibilidad superior al 99 % y ejercicios de continuidad; BIA, RTO, RPO y resultados son **evidencia por obtener**. | Actualizar el análisis de impacto al negocio (BIA); aprobar RTO/RPO; usar redundancia y respaldos inmutables; probar recuperación con terceros. | Una probabilidad moderada con impacto masivo exige pruebas reales y no solamente planes documentados. |
| R-05 | A-05. Cambios y liberaciones | Error humano, código defectuoso, cambio de emergencia o modificación maliciosa | Posible ausencia de aprobación por riesgo, segregación, pruebas, trazabilidad o reversión. **Supuesto por validar.** | Un cambio podría introducir vulnerabilidades, alterar datos o interrumpir los canales digitales. | 3 | 5 | **15 – Alto** | El informe describe transformación de canales; solicitudes, aprobaciones, pruebas y despliegues son **evidencia por obtener**. | Registro único, análisis de riesgo, aprobación independiente, pruebas separadas, controles del pipeline, reversión y revisión posterior. | Los cambios son frecuentes y una falla en componentes compartidos puede afectar a numerosos clientes. |

## 7. Procedimientos de auditoría y evidencia esperada

| ID | Proceso | Control a verificar | Tipo | Procedimiento de prueba | Evidencia esperada | Referencia al marco |
|---|---|---|---|---|---|---|
| R-01 | Autenticación y transacciones | MFA adaptativa, monitoreo antifraude y respuesta | Preventivo, detectivo y correctivo | Inspeccionar la configuración y seleccionar una muestra de alertas y transacciones de riesgo; reejecutar en ambiente autorizado escenarios aprobados y comparar alertamiento, escalamiento y cierre. | Política de autenticación, reglas o modelos vigentes, registros de alertas, casos gestionados, métricas de falsos positivos y tiempos de respuesta. | COBIT APO12 y DSS05; ISO/IEC 27001 A.8.5; ITIL 4 gestión de incidentes. |
| R-02 | Accesos privilegiados | Ciclo de vida de usuarios, PAM y recertificación | Preventivo y detectivo | Comparar, mediante análisis de datos, la población completa de cuentas privilegiadas con personal y contratos vigentes; revisar una muestra de aprobaciones, bajas y recertificaciones. | Exportación generada por el sistema, registros de RR. HH., aprobaciones, evidencia MFA/PAM, bitácoras de sesión y revisiones firmadas. | COBIT APO13 y DSS05; ISO/IEC 27001 A.5.15 y controles asociados de identidad y derechos de acceso. |
| R-03 | Logs y monitoreo | Centralización, integridad y revisión de eventos | Detectivo | Conciliar activos críticos con fuentes conectadas al SIEM; inspeccionar sincronización, retención y acceso; seleccionar alertas y rastrearlas desde su generación hasta el cierre. | Inventario de fuentes, configuración de logs y SIEM, alertas, tickets, escalaciones, registros de revisión y resultados de pruebas de casos de uso. | COBIT DSS05 y DSS02; ISO/IEC 27001 A.8.15 y A.8.16; ITIL 4 monitoreo y gestión de eventos. |
| R-04 | Continuidad y recuperación | BIA, RTO/RPO, respaldos y pruebas de recuperación | Preventivo y correctivo | Inspeccionar BIA y planes; observar o revisar la última prueba; contrastar tiempos y pérdida de datos reales con RTO/RPO; verificar el cierre de desviaciones. | BIA aprobado, mapas de dependencias, inventario de respaldos, reportes de restauración y conmutación, mediciones de tiempo y planes de acción. | COBIT DSS04; ISO/IEC 27001 A.8.13 y A.8.14; ITIL 4 continuidad y disponibilidad del servicio. |
| R-05 | Cambios y liberaciones | Flujo autorizado de cambios y reversión | Preventivo y detectivo | Extraer la población de cambios del periodo; cruzarla con despliegues e incidentes; seleccionar cambios normales y de emergencia para verificar aprobación, pruebas, segregación y revisión posterior. | Tickets de cambio, aprobaciones, resultados de pruebas, evidencia del pipeline, plan de reversión, logs de despliegue y revisión posterior. | COBIT BAI06; ISO/IEC 27001 A.8.32; ITIL 4 habilitación del cambio. |

> **Nota profesional:** los procedimientos anteriores evalúan primero el diseño del control y luego su eficacia operativa. Si el control está documentado pero no hay evidencia de ejecución consistente, no puede considerarse eficaz.

## 8. Interpretación y conclusión preliminar

El riesgo R-01 ocupa el primer lugar porque existe información pública que demuestra la materialización del fraude externo, mientras que los demás riesgos se valoran principalmente por exposición y criticidad. R-02 también es crítico porque el alcance de una cuenta privilegiada eleva el impacto, aunque su vulnerabilidad todavía debe confirmarse. R-03, R-04 y R-05 son altos porque la detección, continuidad y gestión de cambios sostienen la operación de los canales digitales.

Esta matriz no concluye que Bancolombia incumpla ni que sus controles sean ineficaces. Su finalidad es orientar la planeación y definir qué evidencia debe obtenerse. La auditoría proporcionaría **aseguramiento razonable, no absoluto**, y la valoración residual solo se establecería después de aplicar las pruebas autorizadas.

## Referencias

- Bancolombia S.A. (2026). *Informe de gestión 2025*. [Informe oficial](https://www.grupocibest.com/wcm/connect/bf5091ab-dd4e-44fd-9d43-7db2eb451f57/Bancolombia_Informe_de_Gestion_2025.pdf?MOD=AJPERES).
- ISACA. (s. f.). *COBIT*. [Sitio oficial](https://www.isaca.org/resources/cobit).
- International Organization for Standardization. (2022). *ISO/IEC 27001:2022 — Information security management systems — Requirements*. [Sitio oficial](https://www.iso.org/standard/27001).
- PeopleCert. (s. f.). *ITIL 4 Foundation*. [Sitio oficial](https://www.peoplecert.org/browse-certifications/it-governance-and-service-management/ITIL-1/itil-4-foundation-2565).
- Superintendencia Financiera de Colombia. (s. f.). *Circular Básica Jurídica*. [Portal normativo oficial](https://www.superfinanciera.gov.co/). Debe consultarse la versión consolidada vigente antes de ejecutar la auditoría.
