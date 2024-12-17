# README - Dorking Vulnerabilities in Mikhmon and Mikbotam

## **1. General Information**
Mikhmon and Mikbotam are web-based applications used for managing Mikrotik hotspots. However, if default configurations are not changed, these applications are vulnerable to unauthorized access and malicious code execution.

---

## **2. Default Credentials Vulnerabilities**
### Mikhmon
- **Username:** mikhmon  
- **Password:** 1234  

### Mikbotam
- **Username:** admin  
- **Password:** admin  

It is strongly recommended to change these credentials immediately after installation to prevent unauthorized access.

---

## **3. Shell Upload Vulnerability in Mikhmon**
### **Exploitation Steps:**
1. **Login:** Access the application using the default credentials.
2. **Add Router:** Add a new router.
3. **Edit Voucher Template:**
   - Open the "Edit Template" section.
   - Upload an HTML file containing malicious PHP code such as:
     ```php
     <?php phpinfo(); ?>
     ```
4. **Access the Shell:**
   - Click the "QR" button to trigger the uploaded PHP file execution.

---

## **4. Shell Upload Vulnerability in Mikbotam**
### **Exploitation Steps:**
1. **Login:** Access the application using the default credentials.
2. **Edit Bot Core:**
   - Navigate to **Tools > Edit Bot Core**.
   - Insert malicious PHP code such as:
     ```php
     <?php phpinfo(); ?>
     ```
     
     ![image](https://github.com/user-attachments/assets/8a0df024-896c-4d3c-be1a-04f2758cf30a)

3. **Access the Shell:**
   - Access the PHP file using a URL like:
     ```
     {url}/Saldo/Core.php
     ```
    
    ![images](https://github.com/user-attachments/assets/b1b87686-7870-4214-b5ca-9987e4a0c842)

---

## **5. Google Dorking**
### **Mikhmon:**
```
intitle:"MIKHMON" intext:"Please Login"
```

### **Mikbotam:**
```
intitle:"MIKBOTAM" Sign In Forgot password?
```

---

## **6. Security Recommendations**
- **Change Default Credentials:** Immediately after installation.
- **Restrict IP Access:** Allow only known IPs to access the admin interface.
- **Update the Application:** Use the latest available version.
- **Conduct Security Audits:** Perform regular audits to detect potential vulnerabilities.
- **Apply PHP Filter Rules:** Implement specific web server filters to block requests containing potentially malicious PHP code, such as:
  - Denying requests with `eval()`, `system()`, `exec()`, and `shell_exec()`.
  - Blocking file uploads with `.php` extensions unless explicitly required.
  - Inspecting and sanitizing all user inputs.

---

**Warning:** This information is provided for educational and cybersecurity awareness purposes. Misusing this data for illegal activities is a criminal offense and may result in legal consequences.

---

**Copyright:** 2024, Cybersecurity Education.

