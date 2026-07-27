# 🔑 Cheatsheet: SSH en Linux


## 📌 What is SSH?
It's a cryptographic network protocol and software suite widely used in data centers and enterprise networks because it lets you (like an administrator) safely access and control a remote computer or server over an unsecured network. It enables secure device authentication, remote system administration, command execution, and file transfers over insecure networks.

Think of it as a secure, encrypted tunnel: when you type commands into a terminal on your laptop, SSH scrambles those commands, routes them across the internet, and executes them on the destination machine as if you were sitting right in front of its keyboard.

* **Default port:** `22/TCP`
* **Client configuration file:** `~/.ssh/config`
* **Authorized Key File (Server):** `~/.ssh/authorized_keys`

---

## What makes SSH secure?


---

## What does SSH do?


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



---

## 📚 Fuentes y Lecturas Recomendadas 
* [Cloudflare - What is SSH?](https://www.cloudflare.com/learning/access-management/what-is-ssh/)
* [SSH Academy - What is SSH]([https://www.paloaltonetworks.com](https://www.ssh.com/academy/ssh))
* [IBM Documentation - SSH Security Best Practices](https://www.ibm.com)
