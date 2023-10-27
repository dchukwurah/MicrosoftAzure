
# How to Change the app homepage using Azure CLI and Blob Stoage

Use the steps below to configure the home page manually, once we've done this we can create a script to do this automatically:


1. Create fresh VM with user data without app running

2. Install and Login to Azure CLI

3. Create storage account
```
az storage container create \
     --account-name tech254chiedoziestorage \
     --name testcontainer
     --auth-mode login
     --public -access blob
```

4. Create a container (ensure access level with command)
```
az storage container create \
     --account-name tech254chiedoziestorage \
     --name testcontainer
     --auth-mode login
     --public -access blob
```

5. download a cat picture (jpg) using the curl command
```
 curl -o cat.jpg https://images.saymedia-content.com/.image/c_limit%2Ccs_srgb%2Cq_auto:eco%2Cw_700/MTk2NzY3MjA5ODc0MjY5ODI2/top-10-cutest-cat-photos-of-all-time.webp
rename the cat pic

```

6. upload blob

- upload your blob (using this command you can rename your blob as it uploads )

```
az storage blob upload \
--account-name tech254chiedoziestorage \
--container-name testcontainer \
--name cat.jpg \
--file cat.jpg \
--auth-mode login
```

7. Modify homepage file (index.ejs found in views folder) to include cat image in blob storage (use sed command to replace )

- Use sed to search for "</h 2>"

```
sudo sed -i 's/<h2>/<h2>The app is running correctly.</h2><img src="https://tech254chiedoziestorage.blob.core.windows.net/testcontainer/cat.jpg"/>/' ~/repo/app/views/index.ejs
```

## On this step I hit a blocker which is explained at the end of the file.
---

# Other notes

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

- sed to search for '</ h2>'

```sudo sed -i 's/<h2>/<h2>The app is running correctly.</h2><img src="https://tech254chiedoziestorage.blob.core.windows.net/testcontainer/cat.jpg"/>
 /' ~/repo/app/views/index.ejs'
```

## Blockers
- When trying to use sed command I couldn't figure out how to change the image in index.ejs file the sed command did not work due to not having pipes and backslashes in the right place. The below command should fix it.

```
sudo sed -i 's|<\/h2>|<\/h2> \n <img src="https://tech254andrewstorage.blob.core.windows.net/tech254andrewcontainer/catpic.txt" \/>|' ~/repo/app/views/index.ejs
```