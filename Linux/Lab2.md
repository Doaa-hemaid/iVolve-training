# SSH Configuration Setup

## 1. Install OpenSSH Server

Install the OpenSSH server package. This package enables SSH access to your machine.

```bash
sudo apt install openssh-server -y
```

---

## 2. Enable and Start the SSH Service

Ensure that the SSH service is enabled to start on boot and is currently running.

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh  # Verify that the SSH service is active and running
```

---

## 3. Generate SSH Keys

Generate a new RSA key pair (private and public) for secure authentication. The keys will be stored in the specified file `~/.ssh/ivolve_key`.

```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/ivolve_key
```

*Note:* You will be prompted for a passphrase during key generation. This is optional but recommended for added security.

---

## 4. Copy Public SSH Key to Remote Machine

Use `ssh-copy-id` to copy the public key to the remote server's `authorized_keys` file. This allows passwordless login for the user `doaa` on the remote machine with IP `192.168.225.129`.

```bash
ssh-copy-id -i ~/.ssh/ivolve_key.pub doaa@192.168.225.129 
```

---

## 5. Establish SSH Connection

Connect to the remote server using the private key for authentication. If you set a passphrase during key generation, you will be prompted to enter it.

```bash
ssh -i ~/.ssh/ivolve_key doaa@192.168.225.129
```

---

## 6. Configure SSH to Use an Alias

Create an alias to simplify future SSH connections. Edit (or create) the SSH configuration file at `~/.ssh/config` and add the following configuration:

```plaintext
Host ivolve
    HostName 192.168.225.129      # Remote server's IP address
    User doaa                   # Username for login
    IdentityFile ~/.ssh/ivolve_key  # Path to the private key for authentication
```

This configuration allows you to connect to the remote server simply by using the alias `ivolve`.

---

## 7. Test Connection with Alias

Now, test the SSH connection using the alias. The SSH client will automatically use the settings defined in `~/.ssh/config`.

```bash
ssh ivolve
```

---

