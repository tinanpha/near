Step 1 -

-Conduct these steps from your local machine/PC
-Create the private-public key pair:

ssh-keygen -t rsa -C $(hostname) -f "$HOME/.ssh/id_rsa" -P "" ; cat ~/.ssh/id_rsa.pub


-When complete the following should display your public-private keys in your local /.ssh directory

cd ~/.ssh ; ls


-Example listing of the local directory:

scarruthers@Scotts-MBP .ssh % ls
authorized_keys    aws-scott.pem    config        id_ed25519    id_ed25519.pub    id_rsa        id_rsa.pub    known_hosts    known_hosts.old


-The id_rsa.pub file is your newly generated public key

-List the contents of the public key

cat id_rsa.pub


-Example public key contents (we will use this in the next step)

ssh-rsa AAAAB3NzaC1y<REDACTED>Mg5Tr99b1iUG8PMSQ=
  
  Step 2 -

-Akash deployment of Ubuntu server with SSH enabled

-Use the SDL located here: https://github.com/tinanpha/near/blob/main/deploy.yml

-The only edit we need to make is to the ENV public key variable such as:

services:
  ssh:
    image: ubuntu:22.04
    env:
      - 'SSH_PUBKEY=ssh-rsa AAAAB3Nza......'
    command:
      - "sh"
      - "-c"
  
  
  Step 3 -

-Establish SSH connection to Akash deployment

-From the Cloudmos console we need the URL of the provider and the dynamically generated port of the deployment

-Within my example deployment this info can be obtained from the deployment's LEASES tab as shown in the screen shot

-In my example - again as can be seen in screenshot the following would be applicable to my deployment:

---Provider URL - provider.provider-0.prod.ams1.akash.pub
---Deployment port - 30548
  
  ![image](https://user-images.githubusercontent.com/9214156/187659812-dfaf2e58-7bbc-42b9-9244-3f5f0d4f69d5.png)

  
  
