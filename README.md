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


## 4. Fases de implementación

### Fase 1. Preparación del entorno y asignación de identidades

Se preparó el entorno de Microsoft Entra ID para realizar las pruebas de Privileged Identity Management (PIM).

Se utilizaron tres identidades de Mirador de Montepinar:

- **Antonio Recio (arecio):** usuario sincronizado desde Active Directory local.
- **Enrique Pastor(epastor):** usuario sincronizado desde Active Directory local y designado como aprobador.
- **Amador Rivas(arivas):** usuario creado directamente en Microsoft Entra ID.

Se habilitaron las licencias necesarias para trabajar con PIM y se comprobó que las tres identidades podían iniciar sesión. También se verificó el registro de Microsoft Authenticator para los usuarios que participarían en las activaciones.

### Fase 2. Configuración de Privileged Identity Management

Se accedió a Privileged Identity Management desde Microsoft Entra ID y se seleccionó el rol **Helpdesk Administrator (Administrador del departamento de soporte técnico)**.

Este rol permite realizar determinadas operaciones de soporte sobre usuarios, como restablecer contraseñas e invalidar tokens de actualización, sin conceder privilegios de administración global.

Se configuró a Antonio Recio y Amador Rivas con asignaciones elegibles (*Eligible*), de carácter permanente. De este modo, ambos podían solicitar la activación del rol cuando necesitasen realizar una tarea que requiriese esos privilegios.

En la configuración del rol se establecieron las siguientes condiciones:

- Duración máxima de activación: **1 hora**.
- Justificación obligatoria para solicitar la activación.
- MFA obligatoria durante la activación.
- Aprobación obligatoria antes de conceder los privilegios.
- Enrique Pastor como aprobador designado.
- MFA obligatoria para las asignaciones activas.
- Justificación obligatoria para las asignaciones activas.
- Restricción de las asignaciones activas permanentes.

### Fase 3. Solicitud y aprobación de privilegios de Antonio Recio

Se inició sesión con la cuenta de Antonio Recio y se accedió a PIM para consultar sus asignaciones elegibles.

Antonio solicitó activar el rol Helpdesk Administrator durante una hora. Para ello, tuvo que proporcionar una justificación que explicase el motivo de la solicitud.

![Antonio pide privilegios](Screenschots/01_arecioactiv.png)

La petición quedó pendiente de aprobación. Posteriormente, se inició sesión con Enrique Pastor, que accedió a las solicitudes de aprobación de roles de Microsoft Entra y revisó la petición.

Enrique aprobó la activación, añadiendo su propia justificación. Una vez aprobada, Antonio recibió los privilegios de Helpdesk Administrator durante el periodo establecido.

![Antonio tiene privilegios](02_arecioactivado.png)

Se comprobó que el rol aparecía entre sus asignaciones activas y que podía acceder a la opción de restablecimiento de contraseñas de otros usuarios.
![Antonio posee privilegios](03_conrestablecida.png)


### Fase 4. Solicitud y aprobación de privilegios de Amador Rivas

Se repitió el procedimiento con la cuenta de Amador Rivas para comprobar que el flujo de activación funcionaba también con una identidad creada directamente en Microsoft Entra ID.

Amador solicitó la activación temporal de Helpdesk Administrator e incluyó una justificación relacionada con su situación y sus particulares aspiraciones empresariales.

Enrique Pastor recibió la petición y volvió a actuar como aprobador. Tras revisar la solicitud, concedió la activación durante una hora.

![Amador tiene privilegios](04_arivasactivado.png)

Se comprobó que Amador tenía el rol entre sus asignaciones activas y que podía acceder a la opción de restablecimiento de contraseñas.

![Amador posee privilegios](05_arivascon.png)

### Fase 5. Revisión de registros de auditoría

Se consultaron los registros de auditoría de Microsoft Entra ID para revisar la trazabilidad de las operaciones realizadas mediante PIM.

Se localizaron eventos correspondientes a:

- Creación de asignaciones elegibles permanentes.
- Solicitudes de activación de Antonio y Amador.
- Solicitudes de aprobación.
- Aprobaciones realizadas por Enrique Pastor.
- Activaciones completadas correctamente.

Los registros permitieron comprobar que ambas activaciones finalizaron correctamente y conservaron las justificaciones introducidas por los usuarios y el aprobador.

![Registro de auditoria](06_registroauditoria.png)

Durante la primera activación de Antonio se produjo un intento duplicado de solicitud. Al no aparecer una respuesta inmediata en el portal, se volvió a pulsar la opción de activación mientras ya existía una petición pendiente. Microsoft Entra registró el segundo intento con el error `PendingRoleAssignmentRequest`. La solicitud original continuó su proceso y fue aprobada correctamente.
