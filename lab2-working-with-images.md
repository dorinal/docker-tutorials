## Docker Labs

### **Lab 1: Exploring Docker Images**

#### **Objective:**
Learn how to pull, list, and manage Docker images effectively.

#### **Tasks:**

**Pulling Images:**
Pull the **Ubuntu** image from Docker Hub:
  ```bash
  docker pull ubuntu
  ```
Pull the **Alpine** image:
  ```bash
  docker pull alpine
  ```

**Listing Images:**
View all the downloaded images using:
  ```bash
  docker images
  ```

**Inspecting Layers:**
Use the `docker history` command to inspect the layers of the **Ubuntu** image:
  ```bash
  docker history ubuntu
  ```

**Removing Images:**
Remove the **Alpine** image using:
  ```bash
  docker rmi alpine
  ```
Verify that it has been deleted by listing all images again.

**Best Practices:**
Identify unused images and clean up the system using:
  ```bash
  docker system prune
  ```

---

### **Lab 2: Working with Containers**

#### **Objective:**
Understand how to start, list, interact with, and manage Docker containers.

#### **Tasks:**

**Starting a Container:**
Run a container using the **Ubuntu** image in interactive mode:
  ```bash
  docker run -it ubuntu
  ```
Inside the container, run the command:
  ```bash
  echo "Hello from Ubuntu!"
  ```
Exit the container by typing `exit`.

**Listing Containers:**
View running containers:
  ```bash
  docker ps
  ```
View all containers (including stopped ones):
  ```bash
  docker ps -a
  ```

**Stopping and Removing Containers:**
Start a new **Alpine** container:
  ```bash
  docker run -d --name my-alpine alpine sleep 300
  ```
Stop the container:
  ```bash
  docker stop my-alpine
  ```
Remove the container:
  ```bash
  docker rm my-alpine
  ```

**Interactive Mode:**
Run a new **nginx** container in detached mode:
  ```bash
  docker run -d --name my-nginx nginx
  ```
Attach to the running container:
  ```bash
  docker exec -it my-nginx bash
  ```
Run the command:
  ```bash
  ls /usr/share/nginx/html
  ```
Exit the container's shell by typing `exit`.

---

### **Lab 3: Combining Image and Container Management**

#### **Objective:**
Learn how to combine image and container operations to create a workflow.

#### **Tasks:**

Pull the **Python** image:
  ```bash
  docker pull python
  ```

Run a container from the **Python** image and start a Python REPL:
  ```bash
  docker run -it python
  ```

Inside the container, write and execute a simple Python script:
  ```python
  print("Hello, Docker!")
  ```

Exit the container and save its ID using:
  ```bash
  docker ps -a
  ```

Commit the container changes to a new image:
  ```bash
  docker commit <container_id> python-custom
  ```

Run a new container from the **python-custom** image:
  ```bash
  docker run -it python-custom
  ```




## Assignment - Image Management

Problem Statement:

You are tasked with managing and working with Docker images. Perform the following:

- Pull the nginx image from Docker Hub.

- Tag the image with a custom name of your choice.

- Save the tagged image to a tar file for offline use.

- Delete the image from your local machine.

- Load the image back from the tar file and verify its presence using the docker images command.


