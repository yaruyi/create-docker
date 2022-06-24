Using Docker requires both the docker command line client and an appropriate containerisation backend to be installed on your local machine. 
Docker Desktop contains the official Docker backend (Docker Engine)
You can also use minikube and HyperKit 

Set up with minikube and HyperKit:

# For the original script and much more context, check:
# https://dhwaneetbhatt.com/blog/run-docker-without-docker-desktop-on-macos

# Install HyperKit and minikube
brew install hyperkit
brew install minikube

# Install Docker CLI
brew install docker

# Start minikube
minikube start --driver=hyperkit

if you already have minikube with another driver, need to delete it first before start with hyperkit

minikube delete

# Configure minikube to use its Docker daemon
eval $(minikube docker-env)

# Save minikube IP to hostname used by Docker CLI, so it can find the VM
echo "`minikube ip` docker.local" | sudo tee -a /etc/hosts > /dev/null

