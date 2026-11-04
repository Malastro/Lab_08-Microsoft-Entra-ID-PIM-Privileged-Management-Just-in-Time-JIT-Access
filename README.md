# Lab_08-Microsoft-Entra-ID-PIM-Privileged-Management-Just-in-Time-JIT-Access

1. Descripción del proyecto

Referencia: La que se avecina — Temporada 2, episodio 11: «Un datáfono, un suicida y un presidente en las últimas».

En este episodio, Amador Rivas atraviesa una crisis personal y económica después de descubrir la infidelidad de su mujer. La situación termina llevándole a abandonar el domicilio familiar y trasladarse a casa de Leo.

Mientras tanto, en Mirador de Montepinar se desarrolla un conflicto que afecta directamente a toda la comunidad. El presidente acepta una oferta de 60.000 euros a cambio de permitir la instalación de una antena de telefonía móvil en el edificio. Sin embargo, decide quedarse con la mitad del dinero y tratar de ocultar la operación al resto de los vecinos.

Cuando el fraude sale a la luz, estalla el enfrentamiento entre los vecinos. Enrique Pastor inicia una oposición contra Amador para apartarlo de la presidencia y Antonio Recio también decide presentarse como candidato. La gestión de la comunidad queda marcada por la desconfianza y la disputa por el control de las decisiones.

Esta situación sirve como punto de partida para el laboratorio. El episodio muestra cómo una persona con autoridad puede tomar decisiones importantes en nombre de una organización sin que existan controles adecuados sobre el ejercicio de sus responsabilidades.

Tras los problemas de gestión de la comunidad, Mirador de Montepinar S.L. decide revisar el modelo de administración de sus recursos digitales. Durante una auditoría interna, la empresa detecta que algunas cuentas mantienen permisos administrativos permanentes, incluso cuando sus propietarios no necesitan utilizarlos en su actividad diaria.

Esta situación representa un riesgo para la seguridad de la organización: una cuenta comprometida o un uso indebido de privilegios podría permitir realizar cambios críticos sin una necesidad operativa justificada.

Para solucionar este problema, la empresa decide implantar Microsoft Entra Privileged Identity Management (PIM) y adoptar un modelo de acceso Just-In-Time (JIT).

Mediante PIM, los usuarios dispondrán de asignaciones elegibles (Eligible) y tendrán que solicitar la activación de sus privilegios cuando necesiten realizar tareas administrativas. Estas activaciones podrán estar sujetas a requisitos de autenticación multifactor (MFA), justificación, aprobación y una duración limitada.

De esta forma, Mirador de Montepinar S.L. busca evitar que sus administradores mantengan privilegios elevados de manera permanente y establecer un mayor control sobre quién puede ejercerlos, cuándo y bajo qué condiciones.

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

