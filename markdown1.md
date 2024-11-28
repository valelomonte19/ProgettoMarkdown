# Bash files documentation

This documentation outlines the types, functionalities, and usage of bash scripts employed for configuring and deploying our application.

---

## Types of bash files

### 1️⃣ **Bash for NGINX configuration**

**What does it do?**
- Connects the **NGINX reverse proxy** to the **Uvicorn server** hosting the application.

**Why is it important?**
- It ensures that the application endpoints are accessible through the **reverse proxy**, which:
  - manages internal and external traffic;
  - is reachable from **Amazon Web Services (AWS)** and external clients.

---

### 2️⃣ **Bash for application installation on the VM**

- **Modes**:
  - **First deploy**: configures the application from scratch.
  - **Update**: updates the existing application.

**What does it do?**
1. **Operations common to both first deploy and update**:
   - **Remove existing directory**: deletes the application folder if it already exists.
   - **Clone the repository**: executes a `git clone` of the GitHub repository to fetch the latest version of the application.
   - **Configure environment variables**: sets up the environment based on the `config_env` file specific to the environment (e.g., `stg`, `prod`).
   - **Start the Uvicorn server**: launches the server to run the application.

2. **Operations exclusive to the first deploy**:
   - **Create Python virtual environment**: sets up an isolated environment for dependencies.
   - **Install dependencies**: installs the required Python modules.
   - **Update the operating system**: performs system updates.
   - **Install additional software**: configures necessary software, such as **MySQL**.

---

## Executing the bash files

### **First deploy**
Run the following command:
```bash
./deploy_staging.sh --env="stg" --DBPassword="Rootroot24%" --Secret="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" --ip="10.4.124.21" --update=true
```

### **Update**
Run the following command:
```bash
./deploy_staging.sh --env="stg" --DBPassword="Rootroot24%" --Secret="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" --ip="10.4.124.20" --update=false
```


