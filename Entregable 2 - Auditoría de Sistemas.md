# Entregable 2: del riesgo priorizado al plan de auditoría

**Integrante:** Samuel Muriel Meneses  
**Asignatura:** Auditoría de Sistemas (ET0114)  
**Docente:** Juan Duque  
**Naturaleza del documento:** plan de auditoría propuesto. No contiene resultados de pruebas ni hallazgos, dado que la auditoría no ha sido ejecutada.

## 1. Caso, continuidad y riesgo seleccionado

El caso seleccionado es **Bancolombia S.A.** y el sistema de información analizado es el servicio digital **Mi Bancolombia**, junto con los componentes de soporte que se confirmen dentro del alcance. La matriz académica plantea el riesgo de que una cuenta privilegiada permanezca habilitada tras terminar el vínculo de su titular o custodio, lo que podría afectar la confidencialidad, integridad o disponibilidad del servicio. La arquitectura y el estado real de los controles deben comprobarse con evidencia de la entidad.

Se desarrolla **R-02: uso de cuentas administrativas después del retiro**, conservando el identificador y la valoración de la matriz de la sesión 7 ([matriz vigente]).

| Elemento de R-02 | Contenido retomado de la matriz | Qué significa para este plan |
|---|---|---|
| Activo/proceso | **A-02:** baja de cuentas administrativas de componentes que soportan Mi Bancolombia. | Primero se debe confirmar qué componentes e identidades están dentro del universo. |
| Amenaza | Excolaborador que intenta usar sus antiguos privilegios. | Escenario de riesgo, no incidente observado. |
| Vulnerabilidad | **Supuesto por validar:** el aviso de retiro no se integra con la desactivación de cuentas/sesiones y no hay conciliación con personal vigente. | Se probará si el supuesto ocurre; no se redactará como condición real sin evidencia. |
| Consecuencia posible | Acceso administrativo remanente podría permitir consultar información o alterar configuraciones, con exposición de datos o afectación del servicio. | Impacto potencial; no se atribuyen pérdidas, incidentes ni datos comprometidos. |
| Valoración y justificación | **P = 3; I = 5; P × I = 15.** La matriz considera P=3 porque un proceso manual podría omitir una baja, aunque no hay casos comprobados; I=5 porque privilegios podrían permitir cambios en componentes críticos, más allá del alcance de una cuenta ordinaria. | Juicio académico provisional, no frecuencia estadística ni medición de riesgo residual. Debe revalorarse si la evidencia cambia los supuestos. |
| Control actual | No determinado; evidencia por obtener: procedimiento vigente, configuración, registros de bajas y conciliaciones. | No equivale a afirmar que el banco carezca de controles. |
| Control propuesto | Desactivar cuentas/sesiones al retiro y conciliar mensualmente las cuentas privilegiadas con personal y contratos vigentes. | Propuesta del equipo, no control confirmado de Bancolombia. |

**Justificación de prioridad.** R-02 comparte puntaje 15 con R-01, R-04 y R-05; por eso el producto P × I no basta para escogerlo. Se propone profundizar R-02 porque privilegios administrativos pueden ampliar el efecto de un acceso indebido y porque la relación entre retiros, identidades, permisos y registros permite diseñar una prueba trazable. La elección es una priorización académica inicial: antes de una auditoría real se validarían criticidad, exposición efectiva, población, incidentes y controles existentes para confirmar o cambiar el orden.

## 2. Objetivo principal

**Determinar si, para las identidades privilegiadas asociadas a empleados, contratistas y custodios de cuentas compartidas o técnicas en los componentes confirmados dentro del alcance de Mi Bancolombia, el proceso de retiro revoca los accesos y sesiones dentro del plazo aprobado, y si la conciliación periódica detecta y corrige accesos que deban retirarse, para el periodo del 1 de abril al 30 de septiembre de 2026.**

El objetivo se puede responder contrastando fechas de retiro, reglas vigentes, estado de cuentas, revocación de sesiones y cierre de diferencias. No fija un plazo de “24 horas” ni una frecuencia distinta a la que establezca una política aprobada. Si la entidad no tiene una regla documentada o esta no se suministra, se informará como criterio pendiente o limitación; no se calificará como incumplimiento de un plazo inventado.

## 3. Trazabilidad del riesgo al trabajo de auditoría

| Riesgo | Control que se propone evaluar | Criterios | Pregunta de auditoría | Procedimientos principales |
|---|---|---|---|---|
| R-02: acceso privilegiado después del retiro | Baja por evento: notificación, desactivación y revocación de sesión. | C-01; C-02/C-03 como referencias; C-04/C-05 solo si aplican. | ¿El acceso se retira según la fecha, alcance y plazo aprobados? | P-01 diseño; P-02 integridad de población; P-03 eficacia operativa. |
| R-02: cuentas que permanecen activas | Conciliación periódica de identidades privilegiadas con empleados, contratistas y custodios vigentes. | C-01; C-02/C-03; C-04/C-05 solo si aplican. | ¿La revisión cubre el universo y las diferencias se resuelven y verifican? | P-01 diseño; P-02 población; P-04 operación de la conciliación. |

La existencia de un documento o la explicación de una persona no demuestra que un control haya operado. P-01 evalúa principalmente el **diseño**; P-02 a P-04 obtienen evidencia sobre **eficacia operativa**. Un control correctamente diseñado puede no operar; un control ejecutado de forma consistente también puede ser insuficiente si su diseño no cubre todos los accesos relevantes.

## 4. Alcance funcional propuesto

| Delimitador | Alcance y razón |
|---|---|
| Proceso | Terminación o cambio de vínculo, notificación a gestión de identidades, baja de privilegios y sesiones, y revisión/cierre de cuentas remanentes. |
| Sistemas/componentes | Mi Bancolombia y servicios de identidad, administración privilegiada y componentes de soporte que el inventario autorizado identifique como necesarios para este proceso. No se presume producto, proveedor, arquitectura ni integración específica. |
| Población | Retiros efectivos de empleados/contratistas que pudieron tener acceso al universo entre **1 de abril y 30 de septiembre de 2026**, según la fuente de Gestión Humana/contratos; inventario de cuentas/roles privilegiados y eventos de baja, sesiones y conciliación del mismo periodo. Se cruzará la fuente de retiros con los sistemas, no solo con bajas ya registradas en IAM. Si el universo es pequeño, se probará completo. |
| Fecha de corte | Estado de las identidades a **30 de septiembre de 2026**, último día del periodo propuesto. Si la ejecución real empieza después, se definirá un nuevo periodo antes de aprobar el programa. |
| Cuentas no personales | Se incluirán cuentas compartidas, de emergencia o técnicas cuando tengan propietario/custodio humano o puedan seguir siendo conocidas o utilizadas por una persona retirada. Se revisará titularidad y, cuando aplique, reasignación o cambio de secreto. Si no existe inventario fiable, se declarará limitación. |
| Áreas fuente | Gestión Humana/contratos, IAM/PAM, responsables técnicos de los componentes, Seguridad y el dueño del servicio. Legal/Cumplimiento valida aplicabilidad regulatoria. Son custodios o entrevistados; no sustituyen el juicio independiente del auditor. |
| Exclusiones | Cuentas de clientes y pruebas de fraude/transacciones; escaneo de vulnerabilidades, pentest, cambios en producción y revisión de código; otros canales no necesarios para seguir la identidad privilegiada. Si un componente externo o compartido afecta la integridad del universo, se incorpora como dependencia o limitación explícita. |

**Condición de viabilidad:** se requiere autorización escrita, acceso de solo lectura, identificación de custodios y un mapa suficiente de sistemas/cuentas. Los datos se solicitarán minimizados y seudonimizados. Sin fuente completa de retiros y un inventario razonablemente conciliable de privilegios, solo se podrá concluir sobre los registros recibidos, no sobre todo el canal.

## 5. Criterios de evaluación

Se distinguen condiciones internas obligatorias, marcos de referencia y requisitos cuya aplicabilidad legal debe confirmarse. Una referencia no se convierte automáticamente en obligación para Bancolombia: su uso como criterio depende del alcance aprobado, la adopción contractual/interna y, para ISO, de la aplicabilidad declarada en el SGSI.

| ID | Condición que se contrastaría | Fuente y uso | Estado antes del trabajo de campo |
|---|---|---|---|
| C-01 | La terminación, la fecha efectiva, el responsable de notificar, el universo de sistemas, el plazo de baja, la revocación de sesiones, las excepciones y la conciliación tienen reglas vigentes y aprobadas. | Política de control de acceso, procedimiento de retiro, catálogo de roles, matriz de responsabilidades y SLA internos. Es el criterio operativo primario. | **Por solicitar.** Registrar versión, dueño, aprobación y vigencia; no asumir un SLA. |
| C-02 | La identidad y el acceso lógico se administran de forma que los derechos se asignen, revisen, modifiquen y retiren de acuerdo con las reglas aprobadas. | **COBIT 2019, DSS05.04 – Manage user identity and logical access**, como referencia de gestión para el ciclo de identidad y acceso. No determina por sí solo el plazo interno. | Marco de referencia; verificar edición, adopción y material oficial antes de cerrar el programa. |
| C-03 | El control de acceso, la gestión de identidades y los derechos de acceso son pertinentes al ciclo de vida de cuentas privilegiadas. | **ISO/IEC 27001:2022, Anexo A: A.5.15, A.5.16 y A.5.18**, sujeto a la Declaración de Aplicabilidad (SoA) y alcance del SGSI. A.5.16 y A.5.18 son las referencias más directas al ciclo de identidad/derechos; el texto licenciado debe consultarse para evaluar el criterio exacto. | Referencia de auditoría, no presunción de certificación ni de aplicabilidad en la entidad. Confirmar SoA y texto oficial autorizado. |
| C-04 | Si se tratan datos personales y la entidad actúa como responsable, conservarlos con seguridad que evite consulta, uso o acceso no autorizado. | **Ley 1581 de 2012, art. 17 (deberes del responsable)**; verificar texto consolidado, rol y aplicabilidad. | Legal/Cumplimiento confirma el deber pertinente; no se usa para inventar un plazo de baja. |
| C-05 | Los requisitos sectoriales vigentes aplicables a una entidad vigilada incluyen condiciones pertinentes al control evaluado. | **SFC, Circular Básica Jurídica, Parte I, Título IV, Capítulo V**, sujeto a validación de vigencia. | Legal/Cumplimiento confirma versión, disposición precisa, aplicabilidad y relación con el alcance. No se atribuye aquí un numeral no validado. |

**Marcos no seleccionados como criterio independiente.** ITIL 4 se conserva como contexto de operación si facilita entender solicitudes, responsables y trazabilidad, pero no se usa para concluir conformidad: para este riesgo, COBIT DSS05.04, la política de accesos y los controles ISO citados ofrecen una relación más directa. Esta selección evita acumular marcos sin mejorar la prueba.

## 6. Controles y programa de trabajo

Los controles siguientes son **controles objetivo propuestos** a partir de R-02; todavía no se ha verificado que existan en el banco.

| Control objetivo | Responsable sugerido | Tipo | Evidencia que debería dejar |
|---|---|---|---|
| Notificar el retiro efectivo a IAM/PAM y a los dueños de sistemas dependientes. | Gestión Humana/contratos y responsables del proceso. | Preventivo, por evento. | Registro de retiro, identificador seudonimizado, marca de tiempo, aprobación y notificación recibida. |
| Desactivar las identidades privilegiadas y revocar sesiones/tokens dentro del plazo aprobado. | IAM/PAM y administrador autorizado del componente. | Preventivo, por evento. | Estado antes/después, marcas de tiempo, ticket, log de desactivación y evento de sesión revocada. |
| Conciliar periódicamente cuentas/roles privilegiados con personal, contratistas y custodios vigentes; asignar, corregir y cerrar diferencias. | Dueño del servicio con IAM/PAM y Seguridad. | Detectivo y correctivo. | Universo usado, fecha, revisor, excepciones, responsable, acción y evidencia de cierre/reprueba. |

### P-01. Entender el proceso y evaluar el diseño

1. Solicitar C-01 y confirmar aprobación, versión, alcance tecnológico, disparador de baja, fecha efectiva, plazo, tratamiento de sesiones, frecuencia de conciliación, excepciones y roles.
2. Realizar un walkthrough de un caso autorizado de retiro, desde la fuente de Gestión Humana/contratos hasta IAM/PAM y el componente. Si no se obtiene un caso real, el walkthrough se limita a la demostración del diseño y no prueba operación.
3. Inspeccionar configuración/flujo y verificar si todos los sistemas dependientes reciben el aviso, si existe responsable de las cuentas compartidas/técnicas, si la baja cubre sesiones activas y si las excepciones tienen dueño, vigencia y aprobación.
4. Comparar el diseño observado con C-01 a C-05 aplicables. Marcar por separado: diseño adecuado, brecha potencial de diseño o información insuficiente.

**Evidencia esperada:** política y procedimiento aprobados; matriz RACI/roles; diagrama del flujo; catálogo de sistemas; configuración de integración IAM/PAM, cuando exista; ticket/evento de walkthrough; notas de entrevista corroboradas. **Posibles excepciones:** regla sin aprobación o alcance, plazo/frecuencia no definidos, sistema dependiente fuera del flujo, sesiones no cubiertas o cuenta sin propietario.

### P-02. Validar completitud y confiabilidad de la población

1. Obtener de Gestión Humana/contratos los retiros efectivos de personas que pudieron tener acceso al universo, y de IAM/PAM y dueños técnicos exportaciones de cuentas/roles privilegiados, bajas, sesiones y conciliaciones. Registrar custodio, origen, fecha/hora, filtros, campos, zona horaria y totales de control.
2. Validar integridad de reportes mediante consulta/filtros de solo lectura, totales del sistema fuente o control independiente, definiciones de campos e inventario autorizado de componentes. Así se evalúa también si las fuentes cubren el universo y no solo los casos procesados por IAM.
3. Cruzar retiros con identidades y privilegios de los componentes incluidos. Documentar las reglas de emparejamiento (ID interno seudonimizado, alias/cuenta, sistema y fecha), duplicados y registros no asociables.
4. Analizar los registros completos disponibles para detectar cuentas activas a la fecha de corte, falta de evento de baja, sesión/token sin evidencia de revocación, cuentas sin vínculo vigente, privilegios no incluidos o cuenta compartida/técnica sin custodio.

**Evidencia esperada:** extractos fuente, diccionario de datos, filtros/consulta, totales, inventario de sistemas, conciliación seudonimizada y archivo de análisis reproducible. **Posibles excepciones:** población incompleta, diferencia de conteos no explicada, sistemas no mapeados o identidad que no pueda vincularse. Un reporte incompleto limita la conclusión; por sí solo no prueba que una cuenta esté activa.

### P-03. Probar la eficacia operativa de las bajas por evento

1. Definir la población de retiros después de validar P-02. Si es manejable, examinarla completa. De lo contrario, incluir todos los casos con señales de riesgo (cuenta activa al corte, retiro urgente, administrador de alta criticidad, tercero, excepción, sesión no conciliada) y seleccionar el resto por juicio, estratificado por tipo de vínculo/sistema.
2. Para cada elemento seleccionado, rastrear retiro efectivo → notificación → ticket/aprobación → desactivación en IAM/PAM y componentes → revocación de sesión/token → cierre de excepción, si la hubo.
3. Comparar marcas de tiempo con C-01 y comprobar que quien aprobó/ejecutó estaba autorizado. Si el criterio no establece plazo, probar si las acciones ocurrieron y quedaron trazables, pero no calificar oportunidad contra un estándar inexistente.
4. Para cuentas técnicas, compartidas o de emergencia relacionadas, comprobar responsable vigente y evidencia de reasignación/rotación cuando la salida del custodio lo requiera conforme a política.

**Evidencia esperada:** fuente independiente de retiro, solicitud/ticket, logs IAM/PAM y del sistema objetivo, permisos del ejecutor, estado de cuenta/sesión, aprobación de excepción y evidencia de rotación/reasignación si aplica. **Posibles excepciones:** cuenta privilegiada activa luego del plazo aprobado, sesión aún utilizable sin excepción, baja sin cobertura en todos los componentes, cuenta sin custodio o excepción vencida/no aprobada. La selección por juicio no permite proyectar estadísticamente resultados a toda la población.

### P-04. Probar la operación de la conciliación periódica

1. Obtener las revisiones/conciliaciones planificadas en el periodo y contrastar periodicidad, universo, responsable y aprobación contra C-01; no suponer que son mensuales si la norma interna no lo establece.
2. Validar si el revisor recibió el inventario completo de cuentas/roles de todos los componentes incluidos y lo comparó con una fuente vigente de empleados, contratistas y custodios.
3. Examinar todas las diferencias críticas y las que afecten cuentas aún activas; para el resto, seleccionar una muestra por juicio después de conocer volumen y estratos. Rastrear hallazgo → dueño → acción → cambio IAM/PAM → verificación de cierre.
4. Recalcular fechas/transcurso con fuente de solo lectura y comprobar que excepciones temporales tengan responsable, justificación, aprobación y expiración.

**Evidencia esperada:** exportaciones de los universos, actas/revisiones firmadas, aprobaciones, tickets, cambios en IAM/PAM y prueba de cierre. **Posibles excepciones:** conciliación omitida o vencida frente a C-01, población incompleta, revisor sin independencia/autoridad, diferencias abiertas o cierre sin evidencia verificable.

### P-05. Cierre y validación de hechos

Conservar papeles de trabajo que vinculen objetivo, criterio, fuente, procedimiento, población/selección, evidencia, excepción y conclusión. Contrastar hechos con custodios para evitar errores de interpretación, sin delegarles la conclusión. Clasificar resultados como **hecho corroborado, excepción, evidencia insuficiente o limitación**. Solo después de probar se formularía un eventual hallazgo con criterio, condición, causa, efecto y recomendación. Este documento no contiene hallazgos ni resultados.

## 7. Muestreo, calidad y manejo de evidencia

- **Analítica de población:** comparar el universo completo disponible cuando la exportación sea íntegra y se puedan unir fuentes confiables. La cobertura será “población recibida y validada”, no “todos los sistemas del banco” si el inventario no demuestra esa cobertura.
- **Selección detallada:** revisar todos los casos de mayor riesgo y excepciones relevantes; determinar tamaño de la muestra restante después de conocer el volumen, variabilidad y riesgo. La selección por juicio sirve para pruebas orientadas a riesgo; solo un diseño estadístico válido permitiría estimar excepciones de población.
- **Suficiencia y confiabilidad:** preferir registros de sistema, exportaciones controladas y documentos aprobados sobre declaraciones verbales. Verificar origen, periodo, permisos, filtros, integridad y consistencia; corroborar entrevistas con evidencia documental/técnica.
- **Diseño y operación:** la política y la configuración sustentan diseño; tickets, logs, cambios y cierres sustentan operación. Una entrevista o política aislada no prueba que el retiro haya ocurrido.
- **Privacidad y seguridad:** solicitar identificadores mínimos, seudonimizar papeles de trabajo, restringir accesos, conservarlos en repositorio aprobado y aplicar retención acordada. No se necesitan datos de clientes ni detalles de transacciones para probar esta baja.
- **Autorización:** solo consultas e inspecciones de lectura aprobadas. No se cambiarán permisos, no se intentará acceder con cuentas retiradas y no se ejecutarán escaneos o pruebas intrusivas en ambientes reales.

## 8. Responsables, recursos y cronograma

**Integrante:** Samuel Muriel Meneses. Para una ejecución formal, la organización designaría al líder auditor y a los custodios de evidencia, preservando la independencia del equipo.

| Fase propuesta | Trabajo y responsable del equipo | Dependencia/resultado |
|---|---|---|
| Semana 1: planeación | Definir objetivo, alcance, criterios, autorización, solicitud de información y programa de auditoría. | Patrocinador autoriza; Bancolombia confirma custodios, inventario y políticas. |
| Semana 2: levantamiento | Documentar el walkthrough, los roles, el flujo y la confiabilidad inicial de las fuentes. | Gestión Humana/contratos, IAM/PAM, dueño del servicio y Seguridad suministran evidencia de solo lectura. |
| Semana 3: pruebas | Ejecutar conciliación de población, prueba de bajas y revisión de conciliaciones; someter papeles de trabajo a supervisión independiente. | Reportes íntegros, diccionario de campos y repositorio seguro. |
| Semana 4: cierre | Validar hechos, analizar limitaciones, formular conclusión acotada y solicitar respuesta de la administración a eventuales hallazgos. | Custodios corroboran hechos; Legal/Cumplimiento confirma criterios aplicables. |

**Recursos:** políticas/procedimientos vigentes; mapa de identidades y sistemas; exportaciones de retiro, IAM/PAM y sesiones; tickets/logs; herramienta de análisis de datos en solo lectura; repositorio seguro; tiempo de entrevistas. No se requieren credenciales productivas.

## 9. Hechos, supuestos, solicitudes y limitaciones

| Categoría | Declaración |
|---|---|
| Hecho documental | La matriz académica de sesión 7 contiene R-02, P = 3, I = 5 y nivel 15. Esto comprueba lo consignado en la matriz, no que exista una falla en Bancolombia. |
| Supuesto por validar | Puede haber retraso, falta de integración o conciliación incompleta en el retiro de privilegios. No hay evidencia interna recibida que confirme estas condiciones. |
| Información por solicitar | Políticas aprobadas y vigentes; plazo/frecuencia; población de retiros; inventario de sistemas y privilegios; custodios; bajas y sesiones; conciliaciones, excepciones y cierres; SoA de ISO si se usa como criterio. |
| Propuesta del equipo | R-02 como riesgo principal, periodo, objetivo, delimitadores, pruebas, criterios de referencia, muestra y cronograma. No son políticas bancarias ni resultados. |
| Limitación prevista | Sin reglas vigentes no se puede evaluar oportunidad contra un plazo; sin inventario completo no se concluye sobre cobertura; sin registros no se demuestra eficacia operativa. La ausencia de evidencia suficiente se reporta como limitación, no automáticamente como incumplimiento. |

La auditoría daría **aseguramiento razonable y limitado al objetivo, periodo, población y evidencia obtenidos**; no certificaría seguridad total ni cumplimiento integral del banco. Antes de una auditoría formal, Legal/Cumplimiento debe verificar la aplicabilidad y versión vigente de Ley 1581 de 2012 y las instrucciones de la SFC. La Ley 1273 de 2009 no se usa como criterio de tiempo de baja porque no se ha identificado una disposición operativa pertinente para esta prueba.

## 10. Conclusión de la planeación

Se propone una auditoría focalizada en la revocación de accesos privilegiados asociados a retiros y en la conciliación de cuentas remanentes que soportan Mi Bancolombia. La prioridad de R-02 se fundamenta en el impacto potencial de los privilegios y en la posibilidad de probar el proceso mediante fuentes independientes y trazables. La conclusión sobre diseño y eficacia operativa solo podrá emitirse después de confirmar criterios, autorización, universo y evidencia suficiente; este plan no constituye una opinión sobre el estado actual de Bancolombia.

## Referencias

- Duque, J. *Taller: del riesgo priorizado al plan de auditoría*; *Taller: matriz inicial de riesgos de sistemas* y guía del taller, materiales del curso Auditoría de Sistemas (ET0114).
- Material de clase para selección de marcos de auditoría, caso Bancolombia (Entregable 1).
- ISACA. [COBIT 2019 y práctica DSS05.04 de gestión de identidad y acceso lógico](https://www.isaca.org/resources/isaca-journal/issues/2022/volume-3/integrating-mitre-with-cobit). Consultar también el texto de COBIT 2019 utilizado por el curso.
- ISO. [ISO/IEC 27001:2022](https://www.iso.org/standard/27001). Consultar texto oficial autorizado, SoA y aplicabilidad antes de calificar controles del Anexo A.
- República de Colombia. [Ley 1581 de 2012, Gestor Normativo de Función Pública](https://www1.funcionpublica.gov.co/eva/gestornormativo/norma.php?i=49981). Validar texto consolidado, rol del responsable/encargado y aplicabilidad al tratamiento.
- Superintendencia Financiera de Colombia. [Circular Básica Jurídica, Parte I](https://www.superfinanciera.gov.co/publicaciones/10083444/normativanormativa-generalcircular-basica-juridica-ce-parte-i-instrucciones-generales-aplicables-a-las-entidades-vigiladas-10083444/). Revisar capítulo de seguridad de la información y ciberseguridad y confirmar modificaciones posteriores con Legal/Cumplimiento.
- Matriz de riesgos de sesión 7.
