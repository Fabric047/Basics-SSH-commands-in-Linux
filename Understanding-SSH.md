# 🔑 Understanding SSH from scratch


## 📌 What is SSH?
It's a cryptographic network protocol and software suite widely used in data centers and enterprise networks because it lets you (like an administrator) safely access and control a remote computer or server over an unsecured network. It enables secure device authentication, remote system administration, command execution, and file transfers over insecure networks.

Think of it as a secure, encrypted tunnel: when you type commands into a terminal on your laptop, SSH scrambles those commands, routes them across the internet, and executes them on the destination machine as if you were sitting right in front of its keyboard.

* **Default port:** `22/TCP`
* **Client configuration file:** `~/.ssh/config`
* **Authorized Key File (Server):** `~/.ssh/authorized_keys`

---

## What makes SSH secure?
Mathematically and architecturally, modern SSH (SSH-2) is very secure. It replaced older, unencrypted remote login tools like Telnet.

* **Symmetrical & Asymmetrical Encryption:** When you initiate a connection, SSH uses asymmetrical encryption (public/private key pairs) to authenticate parties and safely negotiate a shared secret key. Once established, it switches to fast symmetrical encryption (like AES-256 or ChaCha20) to encrypt all traffic passing through the tunnel.
  
* **Integrity Hashing (HMAC):** Every packet sent through SSH contains a Message Authentication Code. This guarantees that if a bad actor attempts to tamper with or alter data in transit, the receiver instantly drops the connection.
  
* **Key-Based Authentication:** Instead of relying on traditional passwords, SSH allows you to authenticate using SSH keys—a set of two cryptographically linked keys. You keep the private key secret, while the public key sits on the server. The private key never travels over the network, so it is immune to interception.

---

## Where Does SSH Vulnerability Lie?

SSH itself is considered mathematically unbroken but real-world security risks come down to configuration and human error:

| Vulnerability | Why it happens | How to avoid it |
| :--- | :--- | :--- |
| Weak Passwords | Allowing password logins leaves servers vulnerable to automated brute-force scripts | Disable password login and use SSH keys |
| Exposed Private Keys | Leaving private keys unprotected or sharing them unencrypted exposes access | Protect private keys with strong passphrases and strict file permissions |
| Default Port Scanning | The default port of ssh is 22, making it a primary target for automated internet-wide port scanners | Change the SSH port, use fail2ban, or lock access down via a firewall/VPN. |
| Ignoring Host Key Warnings | Blindly accepting new host fingerprints exposes you to Man-in-the-Middle (MitM) attacks | Verify host key fingerprints before connecting to a new server for the first time |

---



---

## 📚 Fuentes y Lecturas Recomendadas 
* [Cloudflare - What is SSH?](https://www.cloudflare.com/learning/access-management/what-is-ssh/)
* [SSH Academy - What is SSH]([https://www.paloaltonetworks.com](https://www.ssh.com/academy/ssh))
* [IBM Documentation - SSH Security Best Practices](https://www.ibm.com)
