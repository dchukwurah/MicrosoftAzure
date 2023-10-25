# Additional Security

- In order to ensure additional security in our db vm we need to change our security group rules to only allow certain traffic, specifically the requests for mongo data from our app instance.

- On Azure, we can do this by being aware of the custom routes and configuring rules with a low number to allow it to have a higher priority on our list

- By default there are rules set up in Azure, we can ensure our rules have a higher weighting by ensuring all traffic other than the rules we set are blocked from access. And also within our rules specifying the IP range we want to accept. This is equivalent to saying we are only allowing access from a specific subnet i.e. (10.0.2.0/24)