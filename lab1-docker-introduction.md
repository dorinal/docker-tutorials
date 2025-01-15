### Installation

**Setup the Repo**
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

**Install Docker Community edition**
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

**Run Hello world**
```
sudo docker run hello-world
```
**Modify the user permission so that you can run docker command without sudo**

For AWS Ubuntu instance
```
sudo usermod -a -G docker ubuntu
```
Logout and Login before executing below commands
---

### **Assignment Tasks**

#### **Task 1: Pull an Image from Docker Hub**
1. Use the `docker pull` command to download the official **nginx** image from Docker Hub:
   ```bash
   docker pull nginx
   ```
2. Verify the image is available locally using the `docker images` command:
   ```bash
   docker images
   ```
3. Run a container from the **nginx** image and expose it on port 8080:
   ```bash
   docker run -d -p 8080:80 nginx
   ```
4. Open a web browser and visit `http://localhost:8080` to confirm nginx is running.

---

#### **Task 2: Build a Custom Docker Image**
1. Create a directory named `custom-nginx`.
2. Inside the directory, create a `Dockerfile` with the following content:
   ```dockerfile
   FROM nginx:latest
   COPY index.html /usr/share/nginx/html/index.html
   ```
3. Add a custom `index.html` file to the same directory. Use the following content for `index.html`:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Custom Nginx</title>
   </head>
   <body>
       <h1>Welcome to My Custom Nginx!</h1>
       <p>This page is served from a custom Docker image built by you.</p>
   </body>
   </html>
   ```
4. Build a new Docker image with the command:
   ```bash
   docker build -t custom-nginx .
   ```

---

#### **Task 3: Run a Container from the Custom Image**
1. Run a container using the newly built `custom-nginx` image and expose it on port 9090:
   ```bash
   docker run -d -p 9090:80 custom-nginx
   ```
2. Open a web browser and visit `http://localhost:9090` to verify the custom nginx page is displayed.

---

#### **Task 4: Push the Image to Docker Hub**
1. Log in to Docker Hub using the `docker login` command:
   ```bash
   docker login
   ```
2. Tag your custom image to match your Docker Hub repository:
   ```bash
   docker tag custom-nginx <your-dockerhub-username>/custom-nginx
   ```
3. Push the image to Docker Hub:
   ```bash
   docker push <your-dockerhub-username>/custom-nginx
   ```
4. Verify the image is successfully uploaded by checking your Docker Hub account.

---

### **Submission Requirements**
1. Screenshots of the following:
   - Pulling the **nginx** image.
   - Running the default nginx container.
   - Custom **index.html** file content displayed in a browser.
   - Docker Hub repository showing the pushed image.
2. Docker commands used for each task, listed step by step.

---

### **Evaluation Criteria**
- Proper execution of all commands and tasks.
- Successful creation and display of the custom web page.
- Correctly tagged and pushed image to Docker Hub.
- Clarity and completeness of screenshots and documentation.

Let me know if you need further assistance or clarifications!
