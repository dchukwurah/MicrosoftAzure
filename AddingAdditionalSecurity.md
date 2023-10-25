# Additional Security

- In order to ensure additional security in our db vm we need to change our security group rules to only allow certain traffic, specifically the requests for mongo data from our app instance.

- On Azure, we can do this by being aware of the custom routes and configuring rules with a low number to allow it to have a higher priority on our list

- By default there are rules set up in Azure, we can ensure our rules have a higher weighting by ensuring all traffic other than the rules we set are blocked from access. And also within our rules specifying the IP range we want to accept. This is equivalent to saying we are only allowing access from a specific subnet i.e. (10.0.2.0/24)

# Removing Public IP
- One way to add additional security is to remove the public IP from our App instance

- Go to app instance with public IP and select the IP from the overview page


# Creating Network Security Rules within your DB network security group (nsg)

- Another way as mentioned is to create and amend rules within the security group

- Go to the DB virtual machine and select networking
![Alt text](AzureDBNetworking1.png)

- Edit the 'source' of the default-allow-ssh rule to only allow traffic from the public subnet
![Alt text](AzureDBNetworking2.png)

- Create another rule to only allow the source of mongodb (port 27027) traffic from the app into the db subnet destination. Ensure the priority is higher than any other rule except the SSH rule

![Alt text](AzureDBNetworking3.png)

- Ensure the deny anything else rule is next, after the two rules specified above.

![Alt text](AzureDBNetworking4.png)

- This means if traffic does not satisy any of these points it cannot connect to the machine.
![Alt text](AzureDBNetworking5.png)


