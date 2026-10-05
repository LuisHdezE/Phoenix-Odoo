# Phoenix · SPEC Maestro

**Repositorio:** `LuisHdezE/Phoenix-Odoo`  
**Estado:** Definición funcional y técnica  
**Tipo de proyecto:** Laboratorio ERP profesional sobre Odoo  
**Fase actual:** Planificación completada · `READY_FOR_CONFIGURATION`  
**Configuración Odoo:** No iniciada  
**Código de aplicación:** No iniciado  
**Desarrollador/learner:** Luis Hernández  

---

## Documentos de planificación vigentes

Phoenix se gobierna actualmente mediante estos documentos:

1. [PHOENIX_SPEC_MASTER.md](./PHOENIX_SPEC_MASTER.md) — alcance funcional y definición maestra.
2. [PHOENIX_BLUEPRINT_PLANNING.md](./PHOENIX_BLUEPRINT_PLANNING.md) — aplicación de la versión multiagente más reciente del Software Development Blueprint, arquitectura, agentes, límites y `STOP_GATE`.
3. [PHOENIX_LEARNING_ROADMAP.md](./PHOENIX_LEARNING_ROADMAP.md) — curso práctico de cero a nivel profesional en el que Luis configura, desarrolla, prueba y despliega Phoenix.

### Regla de aprendizaje

La IA puede actuar como tutor, analista, revisor, debugger y auditor. La configuración y el desarrollo de Phoenix corresponden al desarrollador humano para preservar el objetivo de aprendizaje.

### Baseline técnico aprobado para iniciar el curso

- **Odoo:** 19
- **Edición:** Community
- **Base de datos:** PostgreSQL
- **Estrategia de extensión:** addons propios sin modificar el core
- **Despliegue objetivo:** Oracle Cloud Infrastructure, Ampere A1, Ubuntu 24.04, Docker/Compose, PostgreSQL y reverse proxy/TLS

La configuración real comienza únicamente cuando Luis inicie explícitamente el roadmap de aprendizaje.

---

## 1. Propósito

Phoenix es un laboratorio profesional para aprender, implementar y demostrar competencias reales en Odoo mediante la construcción de un ERP de distribución de extremo a extremo.

El proyecto no debe convertirse en un tutorial genérico ni en una colección de CRUD aislados. Debe reproducir una implementación empresarial coherente, incluyendo análisis funcional, configuración de módulos estándar, desarrollo de personalizaciones, integraciones, seguridad, pruebas, documentación y despliegue.

Phoenix debe servir simultáneamente como:

1. laboratorio técnico de Odoo;
2. laboratorio funcional de procesos ERP;
3. proyecto demostrable de portfolio;
4. preparación para entrevistas y ofertas de empleo Odoo;
5. base reutilizable para futuras soluciones empresariales.

---

## 2. Principios rectores

### 2.1. Reutilizar antes de desarrollar

Antes de crear código propio se debe analizar si el requisito puede resolverse con capacidades estándar de Odoo.

Orden de decisión:

1. configuración estándar;
2. automatización estándar;
3. extensión/herencia de módulos existentes;
4. módulo personalizado;
5. integración externa.

No se modificará directamente el core de Odoo.

### 2.2. Proceso empresarial completo

Cada funcionalidad debe pertenecer a un flujo real y trazable. Phoenix no se evaluará por cantidad de pantallas, sino por la capacidad de ejecutar operaciones completas desde su origen hasta sus efectos financieros y contables.

### 2.3. Separación estándar / personalizado

Toda funcionalidad deberá clasificarse como:

- **STD:** estándar de Odoo;
- **CFG:** configuración de Odoo;
- **CUS:** desarrollo personalizado;
- **INT:** integración externa;
- **REP:** reporting/analítica.

### 2.4. Aprendizaje verificable

Cada bloque debe dejar evidencia verificable mediante código, configuración, pruebas, documentación o escenarios reproducibles.

---

## 3. Empresa de referencia

Phoenix modelará una pequeña o mediana empresa distribuidora que:

- compra mercadería a proveedores;
- mantiene inventario;
- vende a clientes;
- maneja ventas de contado y a crédito;
- administra cuentas por cobrar;
- administra cuentas por pagar;
- opera caja y bancos;
- registra contabilidad de doble partida;
- controla márgenes y rentabilidad;
- requiere autorizaciones según importes y riesgo;
- consume o expone APIs para integrarse con sistemas externos.

El rubro concreto será deliberadamente genérico para que el proyecto pueda reutilizarse en diferentes sectores de distribución.

---

## 4. Objetivos de aprendizaje

Phoenix debe cubrir de forma práctica:

- arquitectura de módulos Odoo;
- Python aplicado a Odoo;
- ORM de Odoo;
- modelos y relaciones;
- herencia y extensión;
- vistas XML;
- acciones y menús;
- dominios y contextos;
- seguridad por grupos;
- ACL;
- record rules;
- workflows y estados;
- automatizaciones;
- cron jobs;
- PostgreSQL;
- QWeb/reportes;
- APIs e integraciones;
- pruebas;
- debugging;
- despliegue;
- análisis funcional;
- documentación de procesos;
- UAT;
- operación de ERP.

---

## 5. Mapa funcional general

```text
CRM
 │
 ▼
Oportunidad
 │
 ▼
Cotización
 │
 ▼
Pedido de venta
 │
 ├─────────────────────────────┐
 │                             │
 ▼                             ▼
Stock disponible          Stock insuficiente
 │                             │
 │                             ▼
 │                       Necesidad de compra
 │                             │
 │                             ▼
 │                         Proveedor
 │                             │
 │                             ▼
 │                       Orden de compra
 │                             │
 │                             ▼
 │                       Recepción de stock
 │                             │
 └───────────────┬─────────────┘
                 ▼
              Entrega
                 │
                 ▼
         Factura de cliente
                 │
                 ▼
        Cuenta por cobrar
                 │
                 ▼
               Cobro
                 │
                 ▼
          Caja / Banco
                 │
                 ▼
          Contabilidad
                 │
                 ▼
      Reportes financieros
```

El flujo de proveedores complementario será:

```text
Necesidad
   ↓
Solicitud / RFQ
   ↓
Orden de compra
   ↓
Recepción
   ↓
Factura proveedor
   ↓
Cuenta por pagar
   ↓
Programación de pago
   ↓
Pago
   ↓
Caja / Banco
   ↓
Conciliación
   ↓
Contabilidad
```

---

# 6. Módulos funcionales

## 6.1. CRM

### Objetivo

Gestionar prospectos y oportunidades hasta convertirlos en clientes y ventas.

### Alcance

- prospectos;
- oportunidades;
- etapas comerciales;
- actividades;
- responsables;
- probabilidad;
- valor esperado;
- conversión a cotización;
- historial comercial.

### Evidencia esperada

Un prospecto debe poder recorrer el ciclo hasta generar una cotización y posteriormente un pedido.

---

## 6.2. Ventas

### Alcance

- clientes;
- cotizaciones;
- pedidos;
- productos;
- listas de precios;
- descuentos;
- condiciones de pago;
- impuestos;
- entrega;
- facturación;
- ventas a crédito.

### Flujo mínimo

```text
Cotización
→ Confirmación
→ Pedido
→ Reserva/entrega
→ Facturación
→ Cuenta por cobrar
→ Cobro
```

---

## 6.3. Compras

### Alcance

- proveedores;
- solicitudes de cotización;
- comparación de proveedores;
- órdenes de compra;
- condiciones de pago;
- recepción;
- facturas de proveedor;
- devoluciones cuando corresponda.

### Personalización principal

**Workflow de aprobación de compras.**

Reglas iniciales de laboratorio:

```text
Compra < umbral A
→ aprobación automática

Compra entre umbral A y B
→ aprobación supervisor

Compra > umbral B
→ aprobación gerencial
```

Los umbrales deben ser configurables y no quedar hardcodeados.

---

## 6.4. Inventario

### Alcance

- productos almacenables;
- categorías;
- unidades de medida;
- almacenes;
- ubicaciones;
- recepciones;
- entregas;
- transferencias;
- ajustes;
- stock actual;
- stock reservado;
- stock disponible;
- stock mínimo;
- reabastecimiento;
- valoración.

### Escenarios

- venta con stock suficiente;
- venta con stock insuficiente;
- recepción parcial;
- entrega parcial;
- devolución;
- ajuste de inventario;
- producto por debajo del mínimo.

---

# 7. Finanzas

## 7.1. Cuentas por cobrar

Phoenix debe permitir conocer en todo momento cuánto debe cada cliente y cuándo vence.

### Requisitos

- facturas de clientes;
- notas de crédito;
- vencimientos;
- términos de pago;
- pagos parciales;
- saldo pendiente;
- facturas vencidas;
- antigüedad de deuda;
- estado de cuenta;
- seguimiento de morosidad;
- conciliación de cobros.

### Indicadores

- total por cobrar;
- corriente;
- vencido;
- vencido 1-30 días;
- 31-60;
- 61-90;
- más de 90 días.

---

## 7.2. Gestión de crédito

Personalización clave de Phoenix.

Cada cliente podrá disponer de:

- límite de crédito;
- saldo utilizado;
- crédito disponible;
- facturas vencidas;
- clasificación de riesgo;
- bloqueo comercial;
- autorización excepcional.

### Regla base

```text
Pedido nuevo
   ↓
evaluar deuda + nuevo pedido
   ↓
¿supera límite?
   ├─ NO → continuar
   └─ SÍ → bloquear confirmación
               ↓
         solicitar aprobación
```

También podrá bloquearse una venta si existen facturas vencidas bajo reglas configurables.

### Requisitos técnicos

- extensión del modelo de cliente;
- extensión del pedido de venta;
- grupos de autorización;
- trazabilidad de excepciones;
- registro de usuario, fecha y motivo de aprobación.

---

## 7.3. Cuentas por pagar

### Requisitos

- facturas de proveedores;
- notas de crédito;
- vencimientos;
- condiciones de pago;
- pagos parciales;
- saldo pendiente;
- obligaciones vencidas;
- aging de proveedores;
- programación de pagos.

### Indicadores

- total por pagar;
- vencido;
- próximos 7 días;
- próximos 30 días;
- obligaciones por proveedor.

---

## 7.4. Tesorería

### Alcance

- caja;
- cuentas bancarias;
- ingresos;
- egresos;
- transferencias;
- cobros;
- pagos;
- conciliación;
- previsión básica de caja.

Phoenix deberá permitir responder:

- cuánto dinero hay disponible;
- cuánto se espera cobrar;
- cuánto se debe pagar;
- qué obligaciones vencen próximamente;
- qué cobros están atrasados.

---

# 8. Contabilidad

## 8.1. Objetivo

Demostrar comprensión de cómo las operaciones comerciales terminan afectando la contabilidad.

Phoenix deberá trabajar con contabilidad de doble partida y permitir seguir la trazabilidad desde una transacción operativa hasta sus asientos.

## 8.2. Alcance

- plan de cuentas;
- diarios;
- asientos;
- cuentas contables;
- impuestos;
- cuentas por cobrar;
- cuentas por pagar;
- caja;
- bancos;
- ingresos;
- gastos;
- costo de ventas;
- inventario;
- ajustes;
- cierres;
- contabilidad analítica cuando resulte útil.

## 8.3. Caso contable obligatorio

Se documentará y probará un escenario completo:

```text
Compra de mercadería
→ recepción
→ factura proveedor
→ cuenta por pagar

Venta
→ entrega
→ factura cliente
→ cuenta por cobrar

Cobro
→ banco/caja
→ cancelación de CxC

Pago proveedor
→ banco/caja
→ cancelación de CxP

Resultado
→ Balance
→ Estado de Resultados
→ Flujo de Caja
```

El objetivo no será crear un motor contable paralelo. Se utilizarán los mecanismos contables de Odoo y se personalizará únicamente cuando exista una necesidad justificada.

---

# 9. Reportes y analítica

Phoenix deberá incluir como mínimo:

- ventas por período;
- ventas por vendedor;
- ventas por cliente;
- ventas por producto;
- margen;
- compras por proveedor;
- rotación de inventario;
- stock bajo;
- valoración de stock;
- cuentas por cobrar;
- aging de clientes;
- cuentas por pagar;
- aging de proveedores;
- balance;
- estado de resultados;
- flujo de caja;
- libro mayor o equivalente;
- indicadores gerenciales.

---

# 10. Dashboard gerencial

Se desarrollará o configurará un tablero que permita observar rápidamente:

```text
VENTAS DEL MES
COMPRAS DEL MES
MARGEN BRUTO

CUENTAS POR COBRAR
CUENTAS POR COBRAR VENCIDAS

CUENTAS POR PAGAR
PAGOS PRÓXIMOS

CAJA + BANCOS

INVENTARIO VALORIZADO
PRODUCTOS CON STOCK BAJO
```

El dashboard deberá permitir navegar desde un indicador hacia los registros que lo originan cuando sea razonable.

---

# 11. Evaluación de proveedores

Personalización propia de Phoenix.

Cada proveedor podrá evaluarse utilizando métricas tales como:

- precio;
- tiempo promedio de entrega;
- entregas tardías;
- cumplimiento de cantidad;
- devoluciones/rechazos;
- volumen comprado;
- calidad;
- score general.

El score deberá derivarse de datos trazables siempre que sea posible.

No se desarrollará un algoritmo complejo en la primera versión. Primero se validará un sistema determinístico y explicable.

---

# 12. Integraciones

Phoenix debe demostrar comunicación con sistemas externos.

## 12.1. Integración entrante

Odoo deberá consumir al menos una API externa.

Ejemplo inicial:

```text
API externa
→ tipo de cambio / dato comercial
→ servicio Phoenix
→ actualización controlada en Odoo
```

La API definitiva se elegirá durante implementación.

## 12.2. Integración saliente

Phoenix deberá exponer o implementar una interfaz que permita consultar o intercambiar información relevante.

Casos candidatos:

- productos;
- disponibilidad;
- clientes;
- pedidos;
- estado de pedidos.

### Requisitos

- autenticación;
- validación;
- manejo de errores;
- logging;
- idempotencia donde corresponda;
- documentación;
- pruebas.

---

# 13. Seguridad

Phoenix debe implementar seguridad real, no solo ocultar botones.

Roles iniciales:

- vendedor;
- supervisor comercial;
- comprador;
- supervisor de compras;
- almacén;
- tesorería;
- contabilidad;
- gerencia;
- administrador.

Se trabajará con:

- grupos;
- ACL;
- record rules;
- permisos por operación;
- segregación de funciones;
- trazabilidad.

Ejemplos:

- un vendedor no deberá aprobar una excepción de crédito propia;
- un comprador no deberá autorizar compras por encima de su límite;
- usuarios no financieros no deberán modificar asientos contables;
- operaciones sensibles deberán registrar responsable y fecha.

---

# 14. Auditoría y trazabilidad

Registrar, cuando corresponda:

- usuario;
- fecha;
- estado anterior;
- estado nuevo;
- motivo;
- aprobación;
- referencia documental.

Procesos especialmente sensibles:

- aprobación de compras;
- excepciones de crédito;
- ajustes de inventario;
- cancelaciones;
- modificaciones financieras;
- pagos.

---

# 15. Arquitectura del desarrollo personalizado

Cuando comience la implementación, los addons propios deberán mantenerse separados del core.

Estructura orientativa:

```text
custom_addons/
└── phoenix/
    ├── __init__.py
    ├── __manifest__.py
    ├── models/
    ├── views/
    ├── security/
    ├── data/
    ├── reports/
    ├── controllers/
    ├── services/
    └── tests/
```

La estructura definitiva podrá dividirse en varios addons si las responsabilidades lo justifican.

Ejemplo futuro:

```text
phoenix_credit_control
phoenix_purchase_approval
phoenix_supplier_score
phoenix_management_dashboard
phoenix_integration
```

Se preferirá modularidad antes que un addon monolítico.

---

# 16. Base de datos

Motor:

**PostgreSQL**

Principios:

- utilizar el ORM de Odoo como vía normal de acceso;
- evitar SQL directo salvo necesidad demostrable;
- no duplicar información disponible en modelos estándar;
- respetar integridad y relaciones;
- mantener migrabilidad;
- documentar campos personalizados.

---

# 17. Edición de Odoo

Antes de implementar deberá ejecutarse un gate técnico para decidir edición y versión objetivo.

Prioridad del laboratorio:

1. permitir desarrollo propio;
2. permitir despliegue económico/gratuito;
3. maximizar capacidades reproducibles;
4. evitar dependencia innecesaria de servicios pagos.

Se evaluará **Odoo Community** como baseline preferente.

Si alguna capacidad financiera, analítica o administrativa relevante depende de Enterprise, se deberá documentar explícitamente y decidir entre:

- alternativa estándar Community;
- extensión propia;
- módulo OCA adecuado;
- demostración temporal Enterprise;
- exclusión consciente.

No se debe ocultar una dependencia Enterprise detrás de una implementación ficticia.

---

# 18. Localización Uruguay

Phoenix debe diseñarse de forma compatible con una futura localización uruguaya, pero la primera fase no declarará cumplimiento fiscal ante DGI hasta haber validado formalmente:

- plan contable;
- impuestos;
- documentos fiscales;
- moneda;
- localización oficial disponible;
- facturación electrónica;
- requisitos legales aplicables.

El laboratorio financiero inicial será funcional y contablemente coherente, pero no se publicitará como solución fiscal uruguaya certificada.

---

# 19. Datos de demostración

Se creará un dataset reproducible con:

- clientes;
- proveedores;
- vendedores;
- compradores;
- productos;
- categorías;
- precios;
- stock inicial;
- cuentas contables;
- condiciones de pago;
- oportunidades;
- pedidos;
- compras;
- facturas;
- cobros;
- pagos.

Los datos no deben contener información personal real.

---

# 20. Escenarios end-to-end obligatorios

## E2E-01 · Venta contado

Oportunidad → cotización → pedido → entrega → factura → cobro → contabilidad.

## E2E-02 · Venta crédito

Cliente con límite → pedido → factura → CxC → vencimiento → cobro parcial → cobro final.

## E2E-03 · Crédito excedido

Pedido → validación de exposición → bloqueo → aprobación/rechazo → auditoría.

## E2E-04 · Compra estándar

RFQ → orden → recepción → factura proveedor → CxP → pago → conciliación.

## E2E-05 · Compra con aprobación

Compra supera umbral → bloqueo → autorización → continuación.

## E2E-06 · Reabastecimiento

Stock mínimo → necesidad → compra → recepción → disponibilidad.

## E2E-07 · Proveedor evaluado

Compras y recepciones → métricas → score → consulta gerencial.

## E2E-08 · Cierre financiero

Operaciones del período → revisión → reportes financieros → validación de saldos.

## E2E-09 · Integración externa

API → validación → actualización Odoo → registro de resultado/error.

---

# 21. Pruebas

Phoenix deberá tener una estrategia de pruebas proporcional al riesgo.

### Niveles

- unitarias;
- lógica de modelos;
- permisos;
- reglas de negocio;
- integraciones;
- escenarios end-to-end;
- UAT funcional.

Especial atención:

- cálculo de crédito disponible;
- autorización de compras;
- pagos parciales;
- efectos de cancelación;
- permisos;
- duplicados;
- errores de API;
- consistencia financiera.

---

# 22. Documentación

El proyecto deberá producir progresivamente:

- SPEC maestro;
- arquitectura funcional;
- mapa de procesos;
- ADRs cuando existan decisiones relevantes;
- matriz STD/CFG/CUS/INT;
- modelo de seguridad;
- documentación API;
- guía de instalación;
- guía de despliegue;
- guía de usuario;
- casos UAT;
- dataset demo;
- handoffs por fase.

---

# 23. Deployment objetivo

El entorno final debe ser accesible públicamente como demostración.

Arquitectura objetivo inicial:

```text
Internet
   ↓
Reverse Proxy / TLS
   ↓
Odoo
   ↓
PostgreSQL
   ↓
Volúmenes persistentes
```

Preferentemente contenerizado para reproducibilidad:

```text
Docker
├── Odoo
├── PostgreSQL
└── reverse proxy
```

Se priorizará una opción gratuita o de muy bajo costo para el laboratorio.

Requisitos:

- HTTPS;
- secretos fuera del repositorio;
- backup;
- persistencia;
- logs;
- configuración reproducible;
- restauración documentada.

---

# 24. Repositorio y gobernanza

## Fase documental actual

El repositorio `Phoenix-Odoo` se utilizará inicialmente solo para especificación y documentación.

No se incorporará código hasta aprobar el alcance inicial y comenzar formalmente la fase de implementación.

## Futuro

Cuando comience desarrollo se definirá:

- estrategia de ramas;
- PRs;
- CI;
- convenciones;
- versionado;
- releases;
- ambientes.

---

# 25. Roadmap

## P0 · Descubrimiento

- definir empresa de referencia;
- fijar versión/edición de Odoo;
- inventariar módulos estándar;
- clasificar STD/CFG/CUS/INT;
- validar alcance contable;
- identificar dependencias Enterprise/OCA;
- definir arquitectura de laboratorio.

**Salida:** alcance implementable aprobado.

## P1 · Entorno base

- Odoo local;
- PostgreSQL;
- Docker;
- repositorio de addons;
- configuración;
- datos demo mínimos;
- primer deployment técnico.

**Salida:** Odoo reproducible local/remoto.

## P2 · Comercial

- CRM;
- clientes;
- productos;
- ventas;
- cotizaciones;
- pedidos.

**Salida:** oportunidad → pedido.

## P3 · Supply Chain

- compras;
- proveedores;
- inventario;
- almacenes;
- reabastecimiento.

**Salida:** compra → recepción → disponibilidad.

## P4 · Finanzas

- facturación;
- CxC;
- CxP;
- cobros;
- pagos;
- caja/bancos;
- conciliación;
- contabilidad.

**Salida:** operación → asiento → saldo → reporte.

## P5 · Personalizaciones

- control de crédito;
- aprobación de compras;
- scoring de proveedores.

**Salida:** addons propios demostrables.

## P6 · Integraciones

- consumo API;
- interfaz externa;
- autenticación;
- errores;
- logging.

**Salida:** Odoo conectado con sistemas externos.

## P7 · Analítica

- dashboard;
- KPIs;
- reportes;
- drill-down.

**Salida:** visión gerencial.

## P8 · Hardening

- seguridad;
- permisos;
- pruebas;
- backup/restore;
- observabilidad;
- documentación.

**Salida:** release candidate.

## P9 · Portfolio

- demo pública;
- dataset;
- screenshots;
- README técnico;
- arquitectura;
- casos de negocio;
- guion de demostración;
- descripción CV/LinkedIn.

**Salida:** proyecto demostrable en entrevistas.

---

# 26. Definition of Done del proyecto

Phoenix se considerará completo cuando un evaluador pueda:

1. acceder a una instancia;
2. iniciar sesión con roles diferentes;
3. registrar una oportunidad;
4. convertirla en venta;
5. entregar productos;
6. facturar;
7. generar una cuenta por cobrar;
8. cobrar total o parcialmente;
9. ejecutar una compra;
10. recibir inventario;
11. registrar una cuenta por pagar;
12. pagarla;
13. observar efectos contables;
14. consultar estados financieros;
15. comprobar controles de crédito;
16. comprobar aprobaciones de compra;
17. consultar score de proveedores;
18. observar indicadores del negocio;
19. ejecutar una integración;
20. revisar código y pruebas de los addons personalizados.

---

# 27. Fuera de alcance inicial

Para evitar que el laboratorio se convierta en un ERP infinito, quedan inicialmente fuera:

- nómina;
- RR. HH. completos;
- manufactura avanzada;
- e-commerce;
- POS;
- logística de última milla;
- fiscalidad uruguaya certificada;
- facturación electrónica DGI productiva;
- aplicación móvil nativa;
- IA generativa como requisito obligatorio.

Podrán incorporarse posteriormente mediante ADR y ampliación del SPEC.

---

# 28. Resultado profesional esperado

Al finalizar Phoenix se deberá poder afirmar y demostrar experiencia práctica en:

> Implementación end-to-end de un ERP sobre Odoo, cubriendo CRM, ventas, compras, inventario, cuentas por cobrar, cuentas por pagar, tesorería, contabilidad, seguridad, automatización, personalizaciones Python, PostgreSQL, integraciones REST, reporting, pruebas y deployment.

La evidencia deberá estar en el repositorio y en una demo reproducible.

---

# 29. Estado de planificación y próximo gate

P0 · Descubrimiento queda suficientemente definido para iniciar el aprendizaje guiado.

Decisiones congeladas para el arranque:

1. Odoo 19 Community como baseline de aprendizaje;
2. PostgreSQL como motor de persistencia;
3. estrategia estándar primero y personalización solo ante gaps demostrados;
4. addons Phoenix separados del core;
5. alcance funcional completo definido;
6. cuentas por cobrar, cuentas por pagar, tesorería y contabilidad incluidas;
7. controles de crédito, aprobación de compras y scoring de proveedores como personalizaciones previstas;
8. integración externa y API propia incluidas;
9. Oracle Cloud Infrastructure como destino de deployment profesional;
10. localización/fiscalidad uruguaya certificada fuera del alcance v1 hasta validación específica.

## STOP GATE

Estado:

```text
READY_FOR_CONFIGURATION
```

A partir de aquí la planificación se detiene.

No se debe:

- instalar o configurar Odoo automáticamente;
- crear addons Phoenix;
- escribir código de implementación;
- realizar deployment;
- adelantar módulos del curso.

El siguiente paso pertenece a Luis y comienza en **Module 0** de `PHOENIX_LEARNING_ROADMAP.md`.

La IA acompañará como tutor y revisor. Luis realizará la configuración y el desarrollo.
