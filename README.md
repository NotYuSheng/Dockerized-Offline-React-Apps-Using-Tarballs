# Dockerized Offline React Apps Using Tarballs
Learn how to cache and reuse React app dependencies offline by generating tarballs. This guide is ideal for environments with limited or no internet access during deployment. You'll use the npm pack command to create tarballs of dependencies and modify your app's Dockerfile to install from these tarballs.

## Prerequisites
- Local installation of Node.js and npm.
- A basic React app with a package.json file.
- Docker installed (if using containerized builds).

## Steps to follow
1. Download the `create-tarballs.sh` script and ensure it is set to executable before running it.
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

## Important Note: EOL Conversion for Shell Scripts

If you encounter issues running the `create-tarballs.sh` script, it may be due to differences in end-of-line (EOL) characters. This is a common issue when shell scripts are created or edited on Windows systems, as they use Windows-style EOL (`\r\n`) instead of the Unix-style EOL (`\n`) required by Linux.

To resolve this issue, ensure the script uses Unix-style EOL. You can convert the script using the tool provided in [NotYuSheng/eol-converter](https://github.com/NotYuSheng/eol-converter). This applies regardless of whether you're running the script on Linux or Docker containers.

#### Quick Fix
If you suspect this issue:
1. Use `dos2unix` (if installed) to convert the script:
 ```bash
 dos2unix create-tarballs.sh
 ```
2. Alternatively, run the [EOL converter tool](https://github.com/NotYuSheng/eol-converter) for a more streamlined fix.
