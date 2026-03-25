# context/business.md — LIVIX: Marketplace de alojamiento universitario

---

## Descripcion
Plataforma B2C2B que conecta estudiantes universitarios (incluidos Erasmus) con propietarios, agencias inmobiliarias y residencias. Mercado inicial: **Zaragoza**. Expansion prevista a otras ciudades universitarias espanolas una vez validado el modelo.

El problema que resuelve: encontrar piso cerca de la universidad es un proceso caotico, disperso en multiples plataformas genericas (Idealista, Fotocasa) que no estan optimizadas para el perfil universitario ni para las necesidades de movilidad internacional (Erasmus).

## Modelo de ingresos
**Fase actual (traccion):** Acceso gratuito para ambos lados del marketplace — objetivo es alcanzar masa critica.

**Monetizacion futura:**
- Estudiantes: Plan Premium (freemium, precio por confirmar)
- Propietarios / Agencias: Suscripcion B2B mensual
- Residencias universitarias: Suscripcion mensual
- Livix Club: acuerdos con negocios locales que ofrecen descuentos a estudiantes registrados (gym, copisteria, ocio nocturno, etc.)

## Estado actual
- Plataforma web operativa
- 0 clientes (propietarios ni estudiantes registrados aun)
- Sin S.L. constituida
- Captacion activa iniciada: scraping de Fotocasa + outreach directo a propietarios

## Stack tecnologico
- Frontend: React + TypeScript
- Backend/DB: Supabase
- Hosting: Vercel
- Construccion asistida: Lovable.dev
- Versionado: GitHub

## Canales de captacion
**Propietarios:**
- Outreach directo (email + WhatsApp) a propietarios extraidos de Fotocasa
- Agencias inmobiliarias locales en Zaragoza (email frio)
- Red de contactos de Eneko

**Estudiantes:**
- TikTok: plan de contenidos de 90 dias activo (10 tipos de contenido definidos)
- LinkedIn: plan de contenidos activo
- Partner dedicado a generacion de trafico universitario
- Grupos de Facebook de Erasmus en Zaragoza
- Asociaciones de estudiantes universitarios (UZ, San Jorge)

## Competidores principales
| Competidor | Tipo | Diferencia |
|---|---|---|
| **Badi** | Marketplace habitaciones | No especializado en universitarios |
| **Uniplaces** | Marketplace estudiantil | Sin presencia fuerte en Zaragoza |
| **Idealista / Fotocasa** | Portales generalistas | No optimizados para Erasmus ni universitarios |
| **Residencias universitarias** | Directo | Sin marketplace que las agregue |
| **Grupos de Facebook** | Informal | Sin verificacion ni confianza |

## Riesgos principales
1. **Chicken-and-egg problem:** Sin propietarios no vienen estudiantes, y viceversa. Es el reto central de fase 0-1.
2. **Estacionalidad:** Demanda concentrada en septiembre (inicio de curso) y enero (Erasmus). Hay que estar posicionado antes.
3. **Competencia de plataformas establecidas:** Idealista y Fotocasa tienen mas trafico SEO.
4. **Retencion de propietarios:** Si no consiguen inquilino rapido, abandonan la plataforma.
5. **Dependencia de un solo mercado:** Si Zaragoza no funciona, la expansion queda bloqueada.
