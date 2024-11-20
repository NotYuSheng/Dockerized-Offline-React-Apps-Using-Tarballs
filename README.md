# Dockerized Offline React Apps Using Tarballs
Learn how to cache and reuse React app dependencies offline by generating tarballs. This guide is ideal for environments with limited or no internet access during deployment. You'll use the npm pack command to create tarballs of dependencies and modify your app's Dockerfile to install from these tarballs.

## Prerequisites
- Local installation of Node.js and npm.
- A basic React app with a package.json file.
- Docker installed (if using containerized builds).

## Steps to follow
1. Download the `create-tarballs.sh` script. Note to set the script to executable.
```
git clone https://github.com/NotYuSheng/Dockerized-Offline-React-Apps-Using-Tarballs.git
cd Dockerized-Offline-React-Apps-Using-Tarballs
```
2. Run the `create-tarballs.sh` script in the directory containing your `package.json`.
```
./create-tarballs.sh
```
This will:
- Install the dependencies using `npm install`.
- Create tarballs for each dependency.
- Save the tarballs in the `tarballs/` directory.
3. Modify the Dockerfile Use the `example/Dockerfile` as a reference for building your app with tarballs.
- Copy the tarballs directory into the Docker image.
- Update the `npm install` command to install from tarballs.
4. Build and run your docker container
