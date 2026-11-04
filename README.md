# Lab_08-Microsoft-Entra-ID-PIM-Privileged-Management-Just-in-Time-JIT-Access

## 1. Descripción del proyecto

Referencia: La que se avecina — Temporada 2, capítulo 24

En este episodio, un fraude económico protagonizado por Amador provoca que Enrique Pastor y Antonio Recio reclamen un cambio en la presidencia de Mirador de Montepinar. 

Esta situación nos sirve para plantear un problema de gobernanza: ¿quién debe tener autoridad para tomar decisiones importantes y bajo qué condiciones puede ejercerla?

Tras los problemas de gestión de la comunidad, Mirador de Montepinar S.L. decide revisar cómo se administran sus recursos digitales. Hasta ahora, determinados usuarios han mantenido permisos administrativos de forma permanente, incluso cuando no necesitan utilizarlos.

Esta situación supone un riesgo. Una cuenta con privilegios elevados puede realizar cambios importantes sin que exista una necesidad operativa inmediata ni un control previo suficiente.

Para solucionar este problema, la organización decide implantar Microsoft Entra Privileged Identity Management (PIM).

A través de PIM, los administradores podrán disponer de asignaciones elegibles y activar sus privilegios únicamente cuando los necesiten. La activación estará sujeta a controles como MFA, justificación, aprobación y una duración limitada.

La analogía del capítulo es una adaptación narrativa del problema de gobernanza; no pretendemos atribuirle al episodio una trama tecnológica que no tiene.

## 2. Objetivos del proyecto
El laboratorio tendrá los siguientes objetivos:
1. Comprender el funcionamiento de Microsoft Entra Privileged Identity Management.
2. Identificar los riesgos de mantener asignaciones administrativas permanentes.
3. Configurar asignaciones elegibles (Eligible) para roles administrativos.
4. Implementar el modelo de acceso Just-In-Time (JIT).
5. Configurar requisitos de MFA, justificación y aprobación para activar privilegios.
6. Establecer límites temporales para las activaciones administrativas.
7. Probar distintos escenarios de solicitud, aprobación, rechazo y expiración.
8. Consultar los registros de auditoría para verificar las operaciones realizadas.
9. Aplicar el principio de mínimo privilegio en la administración del entorno.

## 3. Arquitectura del proyecto

