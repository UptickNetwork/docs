# Connect to Droplet

Click on the started Droplet, and you'll see details about it. At the moment, we're interested in the IP address - this is the address that the Droplet is at on the internet.

To access it, we'll need to connect to it using our previously created private key. From the same folder as that private key, run:

```
ssh -i digital-ocean-key root@<DROPLET_IP_ADDRESS>
```

Now you are connected to the droplet.
