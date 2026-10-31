# Matriz inicial de riesgos de sistemas: Bancolombia S.A.

**Integrante:** Samuel Muriel Meneses  
**Asignatura:** Auditoría de Sistemas (ET0114) - Sesión 7  
**Docente:** Juan Duque  
**Sistema analizado:** Mi Bancolombia y sus procesos de soporte  
**Tipo de documento:** matriz académica inicial de riesgos

## 1. Caso y contexto actualizado

Bancolombia S.A., con sede en Medellín, presta servicios financieros.  
Se delimita el caso a Mi Bancolombia y sus procesos de soporte.  
Se analizan transferencias, bajas de administradores, eventos, recuperación y cambios.  
Los activos incluyen cuentas privilegiadas, registros, datos y versiones en producción.  
Se busca evitar fraude, exposición de datos e interrupciones del servicio.

## 2. Continuidad, alcance y supuestos

Se mantienen **COBIT 2019** para riesgos, **ISO/IEC 27001:2022** para seguridad e **ITIL 4** para operación. Del primer taller se recuperan las solicitudes de revisiones de accesos, registros de seguridad, restauraciones y expedientes de cambios e incidentes.

Se construye una matriz inicial, no una auditoría integral. Quedan fuera otros canales, salvo dependencias indispensables.

- Sin acceso interno ni resultados de pruebas, las debilidades son **supuestos académicos por validar**, no fallas comprobadas de Bancolombia.
- **Control actual no determinado** significa evidencia por obtener, no inexistencia ni eficacia del control.
- P e I son provisionales, no cifras del banco. No se atribuye eficacia a controles ni se calcula riesgo residual real.
- Se propone revisar 90 días de registros. Toda prueba técnica exige autorización formal y alcance definido; los datos deben anonimizarse.

## 3. Criterio de valoración

Se conserva la escala de la guía, con horizonte de doce meses. **Nivel = P × I.** Un producto mayor recibe atención inicial preferente.

| Valor | Probabilidad (P) | Impacto (I) |
|---|---|---|
| 1 | Raro | Consecuencia menor y fácil de corregir |
| 2 | Poco probable | Afecta una operación limitada |
| 3 | Posible | Afecta un proceso relevante o varios usuarios |
| 4 | Probable | Interrumpe un servicio importante o expone información sensible |
| 5 | Muy probable | Puede afectar gravemente la operación, datos críticos o cumplimiento |

**P = 3** es una hipótesis de evento plausible, no una frecuencia comprobada ni una probabilidad real demostrada. Frecuencia de ataques no equivale a probabilidad de éxito. I responde a la consecuencia específica.

## 4. Matriz inicial: cinco activos y cinco riesgos

La matriz identifica cinco activos/procesos y cinco escenarios de riesgo. Las valoraciones son iniciales y académicas; las debilidades se presentan como supuestos por validar, no como hallazgos sobre Bancolombia.

### R-01. Transferencias no autorizadas

| Campo (R-01) | Análisis |
|---|---|
| Activo o proceso | **A-01:** autorización de transferencias desde Mi Bancolombia. |
| Amenaza | Delincuente que intenta operar con credenciales obtenidas mediante suplantación. |
| Vulnerabilidad | **Supuesto:** un flujo de recuperación de acceso no verifica la identidad con un nivel equivalente al del acceso normal. |
| Riesgo y consecuencia | Un tercero podría recuperar el acceso de un cliente y autorizar transferencias aprovechando esa verificación insuficiente, ocasionando pérdidas y reclamaciones. |
| Probabilidad | **3 - Posible.** Requiere datos de la víctima y una recuperación indebida; no hay casos comprobados que sustenten recurrencia. |
| Impacto | **5.** Afectaría dinero e integridad de operaciones financieras. |
| Nivel / prioridad | **3 × 5 = 15.** Efecto directo sobre los recursos del cliente. |
| Control actual | **No determinado; evidencia por obtener:** procedimiento y configuración de recuperación y autorización. |
| Control propuesto | Identidad digital exigirá validar la identidad antes de restablecer factores y autenticación multifactor (MFA) para autorizar transferencias. Seguridad revisará trimestralmente los flujos y excepciones. **Tipo: preventivo.** |
| Evidencia / prueba | **1.** Configuración y diagrama: comprobar validación de identidad y obligatoriedad de MFA. **2.** Registros de recuperaciones y autorizaciones: rastrear una muestra por riesgo y comprobar su ejecución. |
| Referencia | COBIT: servicios de seguridad; ISO/IEC 27001: acceso y autenticación. |

### R-02. Uso de cuentas administrativas después del retiro

| Campo (R-02) | Análisis |
|---|---|
| Activo o proceso | **A-02:** baja de cuentas administrativas de los componentes que soportan Mi Bancolombia. |
| Amenaza | Excolaborador que intenta utilizar sus antiguos privilegios. |
| Vulnerabilidad | **Supuesto:** el aviso de retiro no está integrado con la desactivación de cuentas y sesiones, y no se concilian las cuentas con el personal vigente. |
| Riesgo y consecuencia | Un excolaborador podría conservar acceso administrativo y consultar información o alterar configuraciones, causando exposición de datos o afectación del servicio. |
| Probabilidad | **3 - Posible.** El trámite manual permite omisiones, pero se requiere uso indebido; no hay retiros con acceso vigente comprobados. |
| Impacto | **5.** Los privilegios permitirían modificar componentes críticos, superando el alcance de una cuenta ordinaria. |
| Nivel / prioridad | **3 × 5 = 15.** Alcance administrativo; el desempate requiere conocer los permisos efectivos. |
| Control actual | **No determinado; evidencia por obtener:** inventario de cuentas, novedades de personal y bajas. |
| Control propuesto | RR. HH. notificará fecha y hora del retiro; identidades desactivará cuentas y sesiones en ese momento. El dueño del servicio conciliará mensualmente cuentas privilegiadas con personal y contratos vigentes. **Tipos: preventivo y detectivo.** |
| Evidencia / prueba | **1.** Cuentas y novedades de RR. HH.: cruzar la población completa. **2.** Logs de bajas y conciliaciones: comparar tiempos con el retiro y comprobar el cierre de diferencias. |
| Referencia | COBIT: servicios de seguridad; ISO/IEC 27001: identidades y derechos de acceso. |

### R-03. Actividad administrativa sin trazabilidad suficiente

| Campo (R-03) | Análisis |
|---|---|
| Activo o proceso | **A-03:** registros de acciones administrativas sobre la autorización de transferencias. |
| Amenaza | Usuario interno o atacante que realiza una modificación no autorizada. |
| Vulnerabilidad | **Supuesto:** uno de los componentes no envía sus eventos al monitoreo central y no se alerta la pérdida de esa fuente. |
| Riesgo y consecuencia | Una modificación no autorizada podría permanecer sin detección o sin trazabilidad suficiente, retrasando su contención y la investigación. |
| Probabilidad | **3 - Posible.** La brecha ocultaría actividad indebida; se desconocen su frecuencia y otras barreras de detección. |
| Impacto | **4.** Comprometería detección e investigación sobre un proceso importante, sin demostrar por sí misma pérdidas financieras. |
| Nivel / prioridad | **3 × 4 = 12.** Menor producto, pero la trazabilidad permite investigar los demás escenarios. |
| Control actual | **No determinado; evidencia por obtener:** fuentes, configuración y registros recibidos. |
| Control propuesto | Monitoreo integrará eventos críticos, alertará interrupciones del envío y revisará excepciones diariamente. Probará trimestralmente la detección con eventos autorizados. **Tipo: detectivo.** |
| Evidencia / prueba | **1.** Inventario y configuración: conciliar componentes con fuentes recibidas. **2.** Eventos y tickets: rastrear una interrupción o prueba desde alerta hasta cierre y comparar tiempos con el procedimiento. |
| Referencia | COBIT: seguridad; ISO/IEC 27001: registro y monitoreo; ITIL 4: monitoreo y eventos. |

### R-04. Recuperación incompleta de información transaccional

| Campo (R-04) | Análisis |
|---|---|
| Activo o proceso | **A-04:** restauración de los datos y configuraciones necesarios para recuperar el canal. |
| Amenaza | Falla tecnológica que deja inaccesible el entorno principal. |
| Vulnerabilidad | **Supuesto:** existen copias, pero no se ha probado una restauración completa con validación de integridad de datos. |
| Riesgo y consecuencia | Tras una falla, el servicio podría restaurarse tarde o con información incompleta porque las copias no son recuperables o consistentes, impidiendo operar con saldos y transacciones confiables. |
| Probabilidad | **3 - Posible.** Una copia no probada puede fallar; no probarla no demuestra daño ni recurrencia. |
| Impacto | **5.** Afectaría disponibilidad e integridad de información financiera crítica, incluso con la infraestructura restablecida. |
| Nivel / prioridad | **3 × 5 = 15.** Recuperación de datos y servicio; el desempate requiere el análisis de impacto al negocio. |
| Control actual | **No determinado; evidencia por obtener:** copias, objetivos de recuperación y resultados de restauración. |
| Control propuesto | Continuidad y el dueño del servicio aprobarán RTO (tiempo objetivo de recuperación) y RPO (pérdida tolerable de datos expresada en tiempo) según el análisis de impacto. Infraestructura ajustará respaldos y hará restauraciones trimestrales aisladas; el dueño de los datos validará integridad. **Tipo principal: correctivo.** |
| Evidencia / prueba | **1.** Objetivos y configuración: comparar respaldos con RPO. **2.** Reportes y logs: contrastar tiempo con RTO, pérdida de datos con RPO e integridad; revisar desviaciones. |
| Referencia | COBIT: continuidad; ISO/IEC 27001: respaldos; ITIL 4: continuidad. |

### R-05. Despliegue de cambios sin aprobación independiente

| Campo (R-05) | Análisis |
|---|---|
| Activo o proceso | **A-05:** autorización y despliegue de versiones de Mi Bancolombia en producción. |
| Amenaza | Error humano durante una liberación de software. |
| Vulnerabilidad | **Supuesto:** quien prepara el cambio puede aprobarlo y desplegarlo sin una revisión independiente ni pruebas obligatorias. |
| Riesgo y consecuencia | Un cambio defectuoso podría llegar a producción por falta de revisión y pruebas, alterando el procesamiento de transferencias o interrumpiendo el canal. |
| Probabilidad | **3 - Posible.** La acumulación de funciones permite errores no detectados; sin historial de fallos no se demuestra recurrencia. |
| Impacto | **5.** Un cambio en transferencias podría afectar transacciones críticas, no solo una función visual. |
| Nivel / prioridad | **3 × 5 = 15.** Podría afectar integridad y disponibilidad simultáneamente. |
| Control actual | **No determinado; evidencia por obtener:** permisos de despliegue, solicitudes y aprobaciones. |
| Control propuesto | Cambios exigirá aprobación independiente, pruebas y reversión antes de cada despliegue; el flujo automático bloqueará omisiones. Las emergencias tendrán autorización registrada y revisión al siguiente día hábil. **Tipos: preventivo y detectivo.** |
| Evidencia / prueba | **1.** Permisos y reglas: verificar separación de preparación, aprobación y despliegue. **2.** Tickets, pruebas y logs: conciliar despliegues con cambios autorizados; revisar por riesgo los normales y todas las emergencias. |
| Referencia | COBIT e ISO/IEC 27001: cambios; ITIL 4: habilitación del cambio. |

## 5. Priorización y conclusión

R-01, R-02, R-04 y R-05 obtienen **15**; R-03 obtiene **12**. No se inventa una diferencia numérica para desempatar: primero se solicitarían permisos efectivos, criticidad de componentes, historial de incidentes y objetivos de recuperación. Esto permitiría ajustar P e I y decidir el orden con evidencia. R-03 se revisaría en paralelo por su papel en la detección e investigación.

Primero se comprobaría el **diseño**: respuesta a la debilidad, responsable, frecuencia y criterio. Después, la **operación** mediante registros. Una política firmada no prueba ejecución. Las muestras se definirían conociendo la población, sin atribuir representatividad estadística a una selección por juicio.

Esta matriz orienta la planeación y no contiene hallazgos de incumplimiento. El riesgo residual solo se estimaría tras evaluar controles y limitaciones; la auditoría proporciona aseguramiento razonable, no absoluto.

## Referencias y límites de las fuentes

- Juan Duque. *Taller: matriz inicial de riesgos de sistemas*, sesión 7, y *Guía: cómo construir la matriz inicial de riesgos*. Materiales suministrados en el curso.
- Material de clase para selección de marcos de auditoría, caso Bancolombia (Entregable 1).
- Criterios a contrastar antes de una auditoría formal: [COBIT](https://www.isaca.org/resources/cobit), [ISO/IEC 27001:2022](https://www.iso.org/standard/27001) e [ITIL 4](https://www.peoplecert.org/browse-certifications/it-governance-and-service-management/ITIL-1/itil-4-foundation-2565). Las áreas relacionadas no son equivalencias exactas.

Se omiten estadísticas no revalidadas. Para una auditoría formal deben verificarse la aplicabilidad de las leyes 1581 de 2012 y 1273 de 2009 y las instrucciones consolidadas vigentes de la Superintendencia Financiera sobre seguridad y ciberseguridad. No se emite opinión de cumplimiento.
