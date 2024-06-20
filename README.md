# Microsoft SQL Server 2019 Docker Container

This repository provides a streamlined way to run a Microsoft SQL Server 2019 database within a Docker container. It's perfect for development, testing, or experimenting with SQL Server without the need for a full local installation.

## Prerequisites

* **Docker:** Make sure you have Docker installed and running on your system. You can download it from [https://www.docker.com/](https://www.docker.com/).
* **Docker Compose:** Install Docker Compose to manage multi-container applications. You can get it from [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/).

## Setup Instructions

1. **Clone the Repository:**

   ```bash
   git clone [<repository-url>](https://github.com/ronaldyuwandika/mssql-local.git)
   cd <mssql-local>
   ```

2. **Environment Variables:**

   * Open the `docker-compose.yml` file.
   * Replace the placeholders with your actual values:
     * `<YourStrongPassword>`: Set a strong password for the SQL Server "sa" (system administrator) account. 

3. **Run the Container:**

   ```bash
   docker-compose up -d 
   ```
   This will download the SQL Server image (if not already present) and start the container in detached mode.

4. **Verify the Container:**

   ```bash
   docker ps 
   ```

   You should see the SQL Server container running.

5. **Connect to SQL Server:**
   * **SQL Server Management Studio (SSMS):** Use SSMS or your preferred SQL client. 
   * **Connection Details:**
     * **Server Name:** `localhost` (or the IP address of your Docker host if connecting remotely).
     * **Authentication:** SQL Server Authentication
     * **Login:** `sa`
     * **Password:** The `<YourStrongPassword>` you set earlier.

## Managing the Container

* **Stop:**  `docker-compose stop`
* **Start:** `docker-compose start`
* **Restart:** `docker-compose restart`
* **Logs:** `docker-compose logs -f db` (Follows the logs in real-time)

## Additional Tips

* **Data Persistence:** By default, the SQL Server data is stored in a Docker volume named `dbdata`. This ensures that your database is not lost even if you stop or remove the container.
* **Custom Configuration:** If you need to modify SQL Server settings, you can create a custom configuration file and mount it into the container. Refer to the official SQL Server Docker documentation for details.
* **Security:** Always use a strong password for the "sa" account and consider using firewall rules to restrict access to the SQL Server port (1433) as needed.
* **Advanced Usage:** For more complex setups, you can extend the `docker-compose.yml` file to include additional services (e.g., web servers, application containers) that interact with the SQL Server container.

## Troubleshooting

If you encounter any issues, check the Docker container logs for error messages:

```bash
docker-compose logs -f db 
```
