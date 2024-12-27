# CIS Hardened Image
 
## Pre-requisites
 
1. Ensure that you have access to the “base-ubuntu-user” SSH key access in LastPass
2. Create a “base-ubuntu-user” SSH private key in the following directory ~/.ssh and ensure that file’s permission is 600.
3. Clone “https://github.com/ID-Pal/hardened-ubuntu-image” in the ~/dev-box/ansible/ path
 
## Steps to create Ubuntu hardened instance AMI
 
1. Perform the below command to create a base Ubuntu 20.04 Pro instance in the “Laravel Forge” subnet
 
    ```jsx
    make create-ubuntu-pro
    ```
 
2. Configure SSH block in ~/.ssh/config file
 
    ```jsx
    make configure-ssh
    ```
 
3. Ensure that you can able to access the Ubuntu 20.04 Pro machine
    1. Perform “ssh cis_machine”
    2. Provide your passphrase for “eu-non-prod-jumpbox”
    3. Again provide the passphrase for “base-ubuntu-user” shared in the LastPass mentioned above in Pre-requisites step 1.
4. Perform the below command to apply usg-fixes
 
    ```jsx
    make apply-usg-fixes
    ```
