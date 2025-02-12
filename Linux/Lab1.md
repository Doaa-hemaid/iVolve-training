
# Create User, Group, and Configure Sudo Permissions

## 1. Create a New Group
```bash
sudo groupadd ivolve
```

## 2. Create a New User
```bash
sudo useradd Dev.Doaa.Hemaid
sudo passwd Dev.Doaa.Hemaid
```

## 3. Add User to `ivolve` Group (Secondary Group)
```bash
sudo usermod -aG ivolve Dev.Doaa.Hemaid
```

---

## 4. Configure Sudo Permissions for Installing Nginx Without Password

### Edit the Sudoers File
```bash
sudo visudo
```

### Add the Following Line Under `User Privilege Specification`:
```plaintext
Dev.Doaa.Hemaid ALL=(ALL) NOPASSWD: /usr/bin/apt install nginx
```

---

## 5. Test the Configuration

### Switch to the User
```bash
su - Dev.Doaa.Hemaid
```

### Install Nginx Without Password
```bash
sudo apt install nginx
```

---

This setup allows the user `Dev.Doaa.Hemaid` to install `nginx` using `sudo` without entering a password.
