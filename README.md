# Create  job to automate your app workflow

Depending on your apllication (Programming language), you need to have different tools installed and configured on jenkins

There are 2 ways to install and configure these tools
  - Jenkins plugins
    - Just install plugins(via UI) for your tool
  - Install tools directly on the server.
    - Acess remote server and install
      - If using docker then go into the container and then install them inside the container.

In this repository we are going to see both the ways to install build tools used when we create a job that can be freestyle job or pipeline etc..

## Install Via Jenkins Plugins ( via UI ) for your tool

1. Go to ( In Dashboard ) > Manage Jenkins > System configuration > Tools >
2. You can download whatever tool you want from the mentioned tools ( Now we are going with maven)
3. Go to > Maven Installation and click on add maven
4. Choose from where you want to install it
5. And Click on save.

Boom! Now we have installed the build tool Maven Via UI in jenkins.

## Install tools directly on the server.

1. Let's install node and npm on the server using the cli

```bash
# 1. Update package list
sudo apt update

# 2. Install necessary packages for adding a PPA
sudo apt install -y ca-certificates curl gnupg

# 3. Import the NodeSource GPG key
# (The command depends on your Node.js version; for v20, it's like this)
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg

# 4. Add the NodeSource repository for Node.js v20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_20.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list

# 5. Update package list again to include the new repository
sudo apt update

# 6. Install Node.js (this will also install npm)
sudo apt install -y nodejs

# 7. Verify the installation
node -v
npm -v
```
So same steps goes for installing node nad npm inside the container, The things we need to do first when installing node and npm inside the container are
```bash
docker ps
docker exec -it <Id_of_container> /bash/sh
#Make sure you login as root user rather than jenkins user so above command has to modified a bit
docker exec -u 0 -it <Id_of_container> /bash/sh 
```

Boom! That's it now we can use those tools in our jenkins when we create our job.
