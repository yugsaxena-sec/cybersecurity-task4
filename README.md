# (Note: This README.md contains the guidance, summary of how firewall filters traffic and Commnads list.)

# 🔒 Task 4 – Firewall Configuration using UFW (Linux)

## 🎯 Objective
To configure and test basic firewall rules on Linux using **UFW (Uncomplicated Firewall)**.  
This task demonstrates how to control inbound and outbound network traffic by allowing or blocking specific ports and understanding how firewalls protect systems.

---

## 🧰 Tools Used
- **Operating System:** Kali Linux / Ubuntu  
- **Firewall Tool:** UFW (Uncomplicated Firewall)  
- **Testing Tool:** netcat (nc)

---

## ⚙️ Steps Performed

### 🟢 Step 1: Check and Enable UFW
```bash
sudo apt install ufw -y
sudo ufw enable
sudo ufw status
````

Enabled the firewall and confirmed that it’s active.

📸 *Screenshot:* step1-status.png

---

### 🔴 Step 2: Block Inbound Traffic on Port 23 (Telnet)

```bash
sudo ufw deny 23/tcp
sudo ufw status numbered
```

Blocked Telnet connections since it is an insecure protocol often exploited by attackers.

📸 *Screenshot:* step2-block-port23.png

---

### 🟡 Step 3: Allow SSH (Port 22)

```bash
sudo ufw allow 22/tcp
sudo ufw status numbered
```

Allowed SSH access for secure remote administration.

📸 *Screenshot:* step3-allow-ssh.png

---

### 🔵 Step 4: Test Firewall Rules

```bash
nc -zv localhost 23
```

Attempted to connect to the blocked port (Telnet).
Expected result: **Connection refused** – confirming that the rule works.

📸 *Screenshot:* step4-test1.png

---

### 🔵 Step 5: Test Firewall Rules

```bash
nc -zv localhost 22
```

Attempted to connect to the Open port (SSH).
Expected result: **Connection Succeeded** – confirming that the rule works.

📸 *Screenshot:* step5-test2.png
---

### ⚫ Step 6: Remove Test Rule

```bash
sudo ufw delete deny 23/tcp
sudo ufw status numbered

Deleted the Telnet block rule to restore the original firewall state.

---

### ⚫ Step 7: Remove Test Rule

```bash
sudo ufw delete allow 22/tcp
sudo ufw status numbered
```

Deleted the SSH block rule to restore the original firewall state.