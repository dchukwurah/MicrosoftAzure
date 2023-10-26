# How to stop pm2 process running the node app being run by root

- We will eventually be able to use Azure CLI to update our homepage using an image as a blob stored in azure in a container

- However we faced a blocker as the app is running in the background we weren't able to stop the process in order to relaunch the app

- This is because the app is currently running on port 3000 and only one process can run on a port at a time 

## Personal blocker 

- Initially I didn't see my app folder, this is becsuse I had entered user data and at the start used 'cd ~' this meant that my repo was saved into the root folder as ~ is root for the root user. I was able to access the repo by entering 'sudo su' and then 'cd ~'.


## Checking Pm2 for running services

- After accessing the app folder we used 'pm2 list' to check the pm2 processes running and we couldnt see theres nothing running.

- We couldnt see this initially as its being run by the root user, so we knew it was running but pm2 says its not running

- We could use top but it wouldnt display all the processes only the top ones, ps would only show processes run by our user. The command we then used to see all processes was `ps aux`. This gives all the information about all processes running. Including PID, User and if it's linked to a terminal session.

- This list was very long so in order to get all the information we can combine this command by `|` use `grep` to filter what we want by following it with a keyword.

- Initially we used `node` but as `pm2` is the process manager  running node, it was not successful to run a `sudo kill` command as pm2 will restart it. So instead we had to use `pm2`.

- This highlighted all of the processes containing pm2 and we could then select the one being run by the root user.

- By doing the command `sudo kill <PID>` we can kill the node application and stop the app running. We can check the result by re-running the grep command on pm2 processes.
