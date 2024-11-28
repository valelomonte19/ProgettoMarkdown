# Bash Files Documentation

This documentation outlines the types, functionalities, and usage of bash scripts employed for configuring and deploying our application.

---

## Types of bash Files

### 1️⃣ **Bash for NGINX Configuration**

**What does it do?**
- Connects the **NGINX reverse proxy** to the **Uvicorn server** where the application is running.

**Why is it important?**
- It ensures that the application endpoints are accessible through the **reverse proxy**, which:
  - Manages internal and external traffic (takers).
  - Is reachable from **Amazon Web Services (AWS)** and external clients.

---

### 2️⃣ **Bash for application installation on the VM**

- **Modes**:
  - **Insertion (First Deploy)**: Configures the application from scratch.
  - **Update**: Updates the existing application.

**What does it do?**
1. **Operations common to both first deploy and update**:
   - **Remove existing directory**: Deletes the application folder if it already exists.
   - **Clone the repository**: Executes a `git clone` of the GitHub repository to fetch the latest version of the application.
   - **Configure environment variables**: Sets up the environment based on the `config_env` file specific to the environment (e.g., `stg`, `prod`).
   - **Start the Uvicorn server**: Launches the server to run the application.

2. **Operations exclusive to the first deploy**:
   - **Create Python virtual environment**: Sets up an isolated environment for dependencies.
   - **Install dependencies**: Installs the required Python modules.
   - **Update the operating system**: Performs system updates.
   - **Install additional software**: Configures necessary software, such as **MySQL**.

---

## Executing the Bash Files

### **First Deploy**
Run the following command:
```bash
./deploy_staging.sh --env="stg" --DBPassword="Rootroot24%" --Secret="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" --ip="10.4.124.21" --update=true
```

### **Update**
Run the following command:
```bash
./deploy_staging.sh --env="stg" --DBPassword="Rootroot24%" --Secret="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" --ip="10.4.124.20" --update=false
```


