# SPEC v1.0 — Credo (CRD)

## 1. Concepto
Moneda digital real, usable como dinero, sin blockchain ni gas.
Emisión automática según demanda, con límites anti-inflación.
Segura con criptografía estándar (Ed25519 + SHA-256).

## 2. Unidad
- Nombre: Credo
- Símbolo: CRD
- Decimales: 2 (1 CRD = 100 centavos)

## 3. Seguridad
- Claves Ed25519 por usuario (pública/privada).
- Cada transacción firmada por el emisor.
- Nonce por cuenta → evita doble gasto y replay.
- Hash encadenado por usuario → historial inmutable.
- 2-3 nodos replicados (Raft simple) → alta disponibilidad.
- Open source (MIT) → auditable.

## 4. Formato de transacción
{
  "de": "clave_publica_emisor",
  "a": "clave_publica_receptor",
  "monto": 10.00,
  "nonce": 42,
  "motivo": "pago servicios",
  "firma": "ed25519_firma_hex"
}

## 5. Reglas de emisión automática
- Medición mensual: volumen tx, usuarios activos, monedas atesoradas.
- Si demanda sube → emitir hasta +2% mensual.
- Si demanda baja → retirar hasta -2% mensual (compra y quema con fondo).
- Fondo de reserva: 20% de emisiones → estabilización.
- Fondo comunitario: 10% de emisiones → desarrollo y gobernanza.
- Límite duro: nunca más de +24% anual.

## 6. Gobernanza
- 1 persona = 1 voto (usuarios activos >30 días).
- Cambios de reglas requieren mayoría simple.
- Propuestas públicas en GitHub.

## 7. Comisiones
- Transferencias: 0 CRD.
- Registro: 0 CRD.
- Emisión: 0 CRD (la paga el sistema con el fondo).

## 8. Arquitectura técnica
- Servidor: Node.js + SQLite/PostgreSQL.
- Cliente: PWA (HTML+JS+libsodium.js).
- Replicación: Raft simple (2-3 nodos).
- Hosting gratis: Render + Fly.io + Neon + Cloudflare.
- Código: GitHub, licencia MIT.

## 9. Hoja de ruta
- Semana 1: spec + repo GitHub.
- Semana 2: servidor núcleo (registro, transferencia, saldo).
- Semana 3: cliente PWA + QR.
- Semana 4: replicación + emisión automática.
- Semana 5: lanzamiento beta con 10 usuarios.

## 10. Riesgos y mitigaciones
- Inflación → límites duros ±2%/mes.
- Ataques → firmas Ed25519 + nonces + replicación.
- Baja adopción → foco en comunidad pequeña primero.
- Regulación → consultar normativa local antes de uso masivo.
