# Account Setup

Head over to [Digital Ocean ](https://www.digitalocean.com/)and create an account.

DigitalOcean will want a public key that it can place on any Droplets we start, so that we can access them with a key that we know only we have.

Let's create an SSH keypair now using `ssh-keygen -t rsa -b 4096`

This will ask you for a file where you want to save the key which you can call something like - `digital-ocean-key`.

It'll also ask for a passphrase - feel free to set one if you wish or you could leave it empty. If you created it in the same folder as we've been working out of, you'll see two files - one called `digital-ocean-key` and one called `digital-ocean-key.pub` - these are respectively your private and public keys.

In your DigitalOcean account, on the bottom left hand side, there is a link for `'Security'`. Follow this link, and the next page will have an option to add an SSH key

Click `'Add an SSH key'` and you'll be presented with a dialog to enter your key. Simply copy the contents of your `digital-ocean-key.pub` into the large text box (you can get the contents printed to the terminal with `cat digital-ocean-key.pub`).

#### &#x20; <a href="#create-droplet" id="create-droplet"></a>
