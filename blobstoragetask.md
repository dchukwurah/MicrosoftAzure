
# How to Change the app homepage using Azure CLI and Blob Stoage

Use the steps below to configure the home page manually, once we've done this we can create a script to do this automatically

Create fresh VM with user data without app running

Install and Login to Azure CLI

Create storage account

Create container

download a cat picture (jpg) using the curl command

rename the cat pic

upload blob

make blob public

modify homepage file (index.ejs found in views folder) to include cat image in blob storage (use sed command to replace )

with pm2 kill the app running

start the app using pm2

Test your script works

Once it works: post link in the chat showing modified home page running (along with message: "Modified home page with script")

Make your script called: revert-homepage.sh (save scripts in the app folder). Steps for your script:

change homepage index file back to normal (use sed command)

with pm2 kill the app running

start the app using pm2

remove storage account


create a storage account (we cannot use dashes or hyphens)
```
az storage account create --name tech254chiedoziestorage --resource-group tech254 --location uksouth --sku Standard_ZRS
```
create a container (ensure access level with command)
```
az storage container create \
     --account-name tech254chiedoziestorage \
     --name testcontainer
     --auth-mode login
     --public -access blob
```
- This specialises how we want to authenticate your login
```
--auth-mode login
```

- upload your blob (using this command you can rename your blob as it uploads )
az storage blob upload \
--account-name tech254chiedoziestorage \
--container-name testcontainer \
--name text.txt \
--file text.txt \
--auth-mode login

- to access your blob you need to change the access level 

- downloading a cat image 
https://images.saymedia-content.com/.image/c_limit%2Ccs_srgb%2Cq_auto:eco%2Cw_700/MTk2NzY3MjA5ODc0MjY5ODI2/top-10-cutest-cat-photos-of-all-time.webp

- sudo nano index.ejs


- sed to search for </h2>

sudo sed -i 's/<h2>/<h2>The app is running correctly.</h2><img src="https://tech254chiedoziestorage.blob.core.windows.net/testcontainer/cat.jpg"/>
 /' ~/repo/app/views/index.ejs



## Blockers
- When trying to script, can't figure out how to change the image in index.ejs file (Script not working) 

