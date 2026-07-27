# 🔑 Cheatsheet: SSH en Linux

Mis notas sobre **SSH (Secure Shell)**: teoría rápida, comandos esenciales y configuración de claves.

---

## 📌 ¿Qué es SSH y para qué sirve?
SSH es un protocolo que permite conectar dos computadoras de forma cifrada y segura a través de la red. Se usa principalmente para administrar servidores remotos por línea de comandos.

* **Puerto por defecto:** `22/TCP`
* **Archivo de configuración del cliente:** `~/.ssh/config`
* **Archivo de llaves autorizadas (Servidor):** `~/.ssh/authorized_keys`

---

## 🚀 Comandos de Conexión Básica

| Comando | Descripción |
| :--- | :--- |
| `ssh usuario@IP` | Conectarse a una maquina remota usando contraseña |
| `ssh usuario@IP -p 2222` | Conectarse especificando un puerto diferente al 22 |
| `ssh -i /ruta/id_rsa usuario@IP` | Conectarse usando una llave privada de SSH |

---

## 🔐 Configuración de Autenticación por Llaves (Sin Contraseña)

### 1. Generar tu par de claves en tu máquina
```bash
ssh-keygen -t rsa -b 4096 -C "tu_email@ejemplo.com"
```
> Esto creará dos archivos en tu carpeta `~/.ssh/`:
> * `id_rsa` (Llave privada - **NUNCA LA COMPARTAS**)
> * `id_rsa.pub` (Llave pública - Se copia en el servidor remoto)

### 2. Copiar la llave pública al servidor remoto
```bash
ssh-copy-id usuario@IP
```

---

## 🛠️ Transferencia de Archivos vía SSH (SCP)

Para enviar o descargar archivos entre tu máquina y el servidor:

* **Enviar un archivo local al servidor remoto:**
  ```bash
  scp /ruta/archivo.txt usuario@IP:/ruta/destino/
  ```

* **Descargar un archivo del servidor a tu máquina:**
  ```bash
  scp usuario@IP:/ruta/remota/archivo.txt /ruta/local/
  ```

---

## 💡 Tips de Ciberseguridad / CTFs
* Si encuentras una clave privada (`id_rsa`) en un servidor objetivo durante un CTF, dale los permisos correctos antes de usarla o SSH no te dejará conectar:
  ```bash
  chmod 600 id_rsa
  ssh -i id_rsa usuario@IP
  ```
