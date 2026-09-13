# Taller: Elige el marco correcto para tu auditoría

**Integrante:** Samuel Muriel Meneses
**Asignatura:** Auditoría de Sistemas (ET0114)  
**Docente:** Juan Duque  
**Fecha de entrega:** 16 de septiembre de 2026

## 1. Organización y alcance de la auditoría

**Organización elegida:** Bancolombia S.A.  
**Alcance propuesto:** Gobierno, seguridad y gestión operativa del ecosistema de canales digitales de Bancolombia en Colombia. El alcance comprende la aplicación Mi Bancolombia, la Sucursal Virtual Personas, la Sucursal Virtual Negocios y los componentes que las soportan, como autenticación, pagos, integraciones, proveedores tecnológicos, monitoreo y soporte.

## 2. Contexto

Bancolombia S.A. es una entidad financiera colombiana con domicilio principal en Medellín, dedicada a productos bancarios, créditos, depósitos, pagos y otros servicios financieros. Para prestar estos servicios administra sistemas transaccionales, aplicaciones móviles, sucursales virtuales, cajeros, plataformas de pagos, bases de datos de clientes y herramientas de monitoreo y prevención del fraude. En 2025, 9,4 millones de clientes utilizaron mensualmente sus canales digitales y realizaron por ellos más de 250 millones de transacciones monetarias, equivalentes al 98 % de este tipo de operaciones del banco. Sus principales preocupaciones son el fraude externo, los ciberataques, la pérdida o alteración de datos, la indisponibilidad de los servicios, las fallas de terceros y el incumplimiento regulatorio; de hecho, el 83 % de sus pérdidas operacionales de 2025 estuvo asociado al fraude externo. ([Bancolombia, 2026, pp. 1, 108, 157 y 165](https://www.grupocibest.com/wcm/connect/www.grupocibest.com4955/bf5091ab-dd4e-44fd-9d43-7db2eb451f57/Bancolombia_Informe_de_Gestion_2025.pdf?CVID=pQd3Fh1&MOD=AJPERES))

## 3. Marcos elegidos y orden de aplicación

| Orden | Marco | Función en la auditoría |
|:---:|---|---|
| 1 | **COBIT 2019** | Evaluar el gobierno de TI, la alineación con los objetivos del banco, la asignación de responsabilidades y la gestión integral de riesgos. |
| 2 | **ISO/IEC 27001:2022** | Examinar el Sistema de Gestión de Seguridad de la Información y los controles que protegen la confidencialidad, integridad y disponibilidad. |
| 3 | **ITIL 4** | Verificar cómo se gestionan diariamente los servicios digitales, sus niveles de servicio, incidentes, problemas y cambios. |

### Justificación de la elección y del orden

**Primero aplicaría COBIT 2019**, con énfasis en los objetivos EDM03 (optimización del riesgo), APO12 (gestión del riesgo), APO13 (gestión de la seguridad), DSS04 (continuidad) y MEA03 (cumplimiento). Bancolombia depende de la tecnología para ejecutar casi todas sus transacciones y está sometido a vigilancia financiera, por lo que antes de revisar controles técnicos debo establecer si la Junta y la Alta Gerencia dirigen, priorizan y supervisan adecuadamente los riesgos de fraude, ciberseguridad, continuidad y terceros. COBIT es el punto de partida porque ISO/IEC 27001 e ITIL no cubren con la misma amplitud la alineación entre estrategia, apetito de riesgo, inversiones, responsables y seguimiento corporativo.

**En segundo lugar aplicaría ISO/IEC 27001:2022.** Una vez definidos el alcance, los responsables y los riesgos prioritarios mediante COBIT, evaluaría si el SGSI los convierte en controles verificables. Este marco responde directamente al volumen de datos personales y financieros, al fraude en canales digitales y a la necesidad de mantener la confidencialidad, integridad y disponibilidad. No sería suficiente utilizar únicamente COBIT, porque este ofrece una visión amplia de gobierno, mientras que ISO/IEC 27001 permite profundizar en la evaluación y tratamiento del riesgo de seguridad, los accesos, los incidentes, los proveedores, las vulnerabilidades y la continuidad.

**Finalmente aplicaría ITIL 4.** Aunque un control de seguridad esté bien diseñado, el cliente puede verse afectado si un incidente tarda en resolverse, un cambio causa una caída o no se cumple el nivel de disponibilidad. ITIL permite comprobar la operación cotidiana mediante prácticas de gestión de niveles de servicio, monitoreo y eventos, incidentes, problemas, cambios y mejora continua. No lo usaría como marco principal de seguridad porque su propósito central es la gestión del servicio; lo aplicaría después de COBIT e ISO/IEC 27001 para validar que las decisiones de gobierno y los controles de seguridad funcionan en la prestación real del servicio.

En conjunto, los marcos son complementarios: **COBIT dirige y controla**, **ISO/IEC 27001 protege la información** e **ITIL administra y mejora el servicio**. El orden evita comenzar por tickets o controles aislados sin conocer primero los objetivos, riesgos y responsabilidades que deben orientarlos.

## 4. Evidencia que solicitaría al equipo de TI

### 4.1. COBIT 2019

1. **Gobierno, estrategia y responsabilidades:** plan estratégico de TI, mapa de procesos, matriz RACI y políticas aprobadas, junto con las actas de los últimos doce meses del Comité de Riesgos o de Tecnología. Verificaría que existan responsables, decisiones, recursos y seguimiento para los riesgos de fraude digital, indisponibilidad, ciberseguridad y terceros.
2. **Gestión y monitoreo del riesgo:** registro actualizado de riesgos de los canales digitales, con activo o servicio afectado, causa, probabilidad, impacto, riesgo residual, apetito o tolerancia, dueño, tratamiento, fecha y estado. Lo contrastaría con los indicadores clave de riesgo y los reportes presentados a la Alta Gerencia para comprobar que los riesgos críticos generan acciones oportunas.
3. **Cumplimiento y aseguramiento:** matriz que relacione las obligaciones de la Superintendencia Financiera y de protección de datos con los controles internos, sus responsables y evidencias; además, informes de auditoría interna o externa y seguimiento a los planes de acción. Revisaría que los hallazgos no estén vencidos ni se cierren sin validar su eficacia.

### 4.2. ISO/IEC 27001:2022

1. **Base documental del SGSI:** alcance vigente, inventario y clasificación de activos, diagramas de flujo de información, metodología y última evaluación de riesgos, plan de tratamiento y Declaración de Aplicabilidad. Comprobaría que Mi Bancolombia, las sucursales virtuales, sus datos e integraciones con terceros estén incluidos y que cada riesgo tenga controles y responsables.
2. **Gestión de identidades y accesos:** matriz de roles, revisiones periódicas de privilegios y una muestra de altas, modificaciones y retiros de usuarios y cuentas administrativas de los últimos seis meses, acompañada de registros de autenticación multifactor. Evaluaría mínimo privilegio, segregación de funciones y retiro oportuno de accesos.
3. **Operación y respuesta de seguridad:** últimos informes de escaneo de vulnerabilidades y pruebas de penetración con sus remediaciones; alertas y registros del SOC/SIEM; expedientes de incidentes y resultados de pruebas de respaldo, restauración y recuperación. Verificaría tiempos de corrección, trazabilidad, aprendizaje del incidente y capacidad real de recuperación.

### 4.3. ITIL 4

1. **Catálogo y niveles de servicio:** catálogo de Mi Bancolombia y las sucursales virtuales con dueño, criticidad, horario, dependencias, SLA/SLO y métricas; además, tableros de disponibilidad y rendimiento de los últimos doce meses. Compararía las interrupciones reales con los niveles acordados y con el indicador público de disponibilidad superior al 99 % reportado por el banco.
2. **Incidentes y problemas:** muestra de incidentes críticos y de alta prioridad, con hora de detección, clasificación, escalamiento, comunicaciones, restauración y cierre; también análisis de causa raíz, errores conocidos y soluciones permanentes. Calcularía tiempos de respuesta y recuperación, y verificaría que los incidentes repetitivos se gestionen como problemas.
3. **Cambios y liberaciones:** muestra de cambios realizados durante los últimos seis meses en la aplicación y las sucursales virtuales, con evaluación de riesgo, aprobación, pruebas, segregación de funciones, plan de reversión y revisión posterior. La cruzaría con incidentes y caídas para identificar cambios no autorizados o implementaciones que hayan afectado el servicio.

## 5. Conclusión

La secuencia COBIT–ISO/IEC 27001–ITIL permite revisar a Bancolombia desde tres niveles conectados: dirección y control empresarial, protección de la información y operación del servicio. Así, los hallazgos podrían priorizarse según su impacto en los clientes, la continuidad, las pérdidas por fraude y el cumplimiento, y no solamente por la existencia formal de documentos o controles.

## Referencias

- Bancolombia S.A. (2026). *Informe de gestión 2025*. [https://www.grupocibest.com/corporativo/informe-gestion](https://www.grupocibest.com/corporativo/informe-gestion)
- ISACA. (s. f.). *COBIT*. [https://www.isaca.org/resources/cobit](https://www.isaca.org/resources/cobit)
- International Organization for Standardization. (2022). *ISO/IEC 27001:2022: Information security management systems—Requirements*. [https://www.iso.org/standard/27001](https://www.iso.org/standard/27001)
- PeopleCert. (s. f.). *ITIL 4 Foundation*. [https://www.peoplecert.org/browse-certifications/it-governance-and-service-management/ITIL-1/itil-4-foundation-2565](https://www.peoplecert.org/browse-certifications/it-governance-and-service-management/ITIL-1/itil-4-foundation-2565)
