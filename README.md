# Enabling TCP Connections to PostgreSQL

This document provides step-by-step instructions to enable TCP connections to PostgreSQL and configure the firewall settings. Follow these steps carefully to ensure remote clients can connect to your PostgreSQL database securely.

---

## 1. Modify PostgreSQL Configuration File

### Steps:
1. Navigate to the PostgreSQL data directory:
   ```
   C:\Program Files\PostgreSQL\16\data
   ```
   (Replace `16` with your installed PostgreSQL version.)

2. Open the `postgresql.conf` file in a text editor.

3. Locate the `listen_addresses` parameter and modify it:
   ```
   listen_addresses = '*'
   ```
   - To restrict access to specific IP addresses, provide a comma-separated list of IPs instead of `*`.

4. Save the changes and close the file.

---

## 2. Modify `pg_hba.conf` File

### Steps:
1. Open the `pg_hba.conf` file located in the same directory as `postgresql.conf`.

2. Add the following entry to allow TCP connections:
   ```
   host    all             all             0.0.0.0/0               md5
   ```
   - This configuration allows all users (`all`) to connect to all databases (`all`) from any IP address (`0.0.0.0/0`) using password authentication (`md5`).
   - Adjust the IP range and authentication method as necessary for your security requirements.

3. Save the changes and close the file.

---

## 3. Restart PostgreSQL

### Steps:
1. Open the Windows Services Manager.
2. Locate the service named `postgresql-x64-16` (or a similar name based on your version).
3. Restart the PostgreSQL service to apply the changes.

---

## 4. Configure Firewall (Optional)

### Steps:
1. Open the firewall settings on your system.
2. Allow incoming connections to the PostgreSQL port (default: `5432`).
3. Save the firewall configuration.

---

## Security Tips
- Use strong passwords for all database users.
- Limit the IP address range in the `pg_hba.conf` file to trusted clients.
- Regularly monitor and update PostgreSQL to apply security patches.

---

After completing these steps, remote clients should be able to connect to the PostgreSQL database using the appropriate connection string and credentials.

---

## Additional Resources
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

---

### Example Connection String
```
postgresql://<username>:<password>@<host>:5432/<database>
```

### Notes:
After installed postgresql Add bin directory to the PATH environment variable

```
   C:\Program Files\PostgreSQL\16\bin
   ```
```
   C:\Program Files\PostgreSQL\16\data
   ```

### Postgresql Version Check
```
postgres --version
```
