# Blob storage

## What is Blob Storage
- Blob stands for Binary Large Object Storage is a type of storage used as way to store unsturctured data.

- within a storage account within a resource group

- cheapest form of blob storage is archival

- blobs are stored in containers ( think of throwing clothes (blobs) on the bed (container).

- if you are accessing blobs a lot then the access tier = frequent= hot

- subsequent tiers are cold and archival being the lowest

- if you want to make access archival you need to do it manually and say its archival

- this is for if youre not acessing it for months/years

- you have to make sure its the right avcess group othersise it will cost more. e.g. a regularly accessed website would be in the hot tier if not it would cost more to grab the data

# using Azure CLI
- creating a storage account , creating a container, finding and downloading the blob "cat.jpg"

- you can vhange the access level also via command

- types of redundancy : 
- LRS (locally redundant storage 3 copies, 1 availavility zone)
- ZRS (sone redundant storage) a copy in each azailability zone

- There are also different tiers