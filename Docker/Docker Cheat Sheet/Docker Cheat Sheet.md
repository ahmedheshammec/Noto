
## How to Activate Docker Command Line Tools if You Moved the App to Another Hard Drive?

❖ Open `.zshrc` File and Add the Following Line:
```plaintext
export PATH=$PATH:"/Volumes/Samsung T5/Apps Installed (To Free Space)/Docker.app/Contents/Resources/bin/"
```
❖ Then Restart the Terminal for Things to Take Effects.

## Where Does Docker Store It's Files so We Can Create a Symbolic Link to Save some Space?
Docker typically stores container data in a specific directory on your system. The default location varies depending on your operating system. Here’s how you can find it:

### On macOS and Windows (using Docker Desktop):
Docker Desktop stores its data within a virtual machine. The files are generally located in a hidden directory inside your home directory:
- **Docker Desktop for macOS:** 
  - The data is usually stored in: `~/Library/Containers/com.docker.docker/Data/vms/0`
- **Docker Desktop for Windows:** 
  - The data is typically stored in: `C:\Users\<YourUserName>\AppData\Local\Docker`

However, the actual container data (like volumes, images, etc.) is stored inside the Docker virtual machine. To access this, you would usually need to use Docker commands.

### On Linux:
Docker stores container and image data in the `/var/lib/docker` directory by default. If you’ve installed Docker on an external drive, it may use a different location. 

### Finding the Docker Data Directory:
1. **Check Docker Info:**

   - Run the following command to get information about Docker’s storage:
```plaintext
docker info | grep "Docker Root Dir"
```

   - This command will output the path where Docker is storing its files.

2. **Custom Data Directory:**

   - If Docker was configured with a custom data directory, you would need to check the Docker daemon configuration. This is usually found in `/etc/docker/daemon.json` on Linux systems. If it has been moved due to your external hard drive setup, you might have specified it during installation or in the Docker settings.

### Accessing Docker Files:
- You can access and manage Docker containers, images, volumes, and other data using Docker CLI commands. For example:
  - **List containers:** `docker ps -a`
  - **List images:** `docker images`
  - **Inspect a container:** `docker inspect <container_id>`