# Servicio Mínimo de Registro de Usuarios (NestJS + PostgreSQL + Docker)

Servicio para registro de usuarios con interfaz web integrada, usando **NestJS**, **PostgreSQL** y **Docker Compose**.

## 🚀 Inicio Rápido (con Docker)

1. Levanta los contenedores:
   ```bash
   docker compose up --build
   ```

2. Abre tu navegador en:
   👉 **http://localhost:3000**

   Verás el formulario web listo para registrar nuevos usuarios directamente en la base de datos PostgreSQL.

---

## 💻 Interfaz Web

- **Formulario interactivo:** Pide nombre, correo electrónico y contraseña.
- **Validaciones:** Comprueba formatos y longitud mínima de contraseña (8 caracteres) tanto en cliente como en servidor.
- **Feedback visual:** Mensajes de éxito y error en pantalla sin recargar la página.

---

## 📬 Endpoint REST API

También puedes consumir el servicio vía API si lo prefieres:

### `POST /users/register`

```bash
curl -X POST http://localhost:3000/users/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Carlos Gomez",
    "email": "carlos@example.com",
    "password": "passwordSeguro123"
  }'
```

#### Respuesta esperada (201 Created):
```json
{
  "message": "User registered successfully",
  "user": {
    "id": "e4b9b9c0-1234-4567-89ab-cdef01234567",
    "name": "Carlos Gomez",
    "email": "carlos@example.com",
    "createdAt": "2026-11-17T21:00:00.000Z"
  }
}
```

> **Nota de seguridad:** La contraseña se almacena de forma segura en PostgreSQL con hash `bcrypt` y nunca se expone en la respuesta.
