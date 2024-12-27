# hardened-ubuntu-image
A pre-configured CIS-1 hardened Ubuntu image with enhanced security measures, optimized for secure deployment in production environments. This repository includes automated scripts and configurations for system hardening, compliance with best practices, and mitigation of common vulnerabilities.

## Pre-requisites

1. Ensure that you have access to the “base-ubuntu-user” SSH key access in LastPass
2. Create a new “base-ubuntu-user” SSH private key in the following directory **~/.ssh** and ensure the file’s permission is 600.
3. Clone “https://github.com/ID-Pal/hardened-ubuntu-image” in the ***~/dev-box/ansible/*** path

## Steps to create Ubuntu hardened instance AMI

1. Perform the below command to create a base Ubuntu 20.04 Pro instance in the “Laravel Forge” subnet in the EU region

    ```bash
    make create-ubuntu-pro
    ```

2. Configure SSH block in ~/.ssh/config file

    ```bash
    make configure-ssh
    ```

3. Ensure that you can able to access the Ubuntu 20.04 Pro machine
    - Perform command `ssh cis_machine`
    - Provide your passphrase for “**eu-non-prod-jumpbox**”
    - Again provide the passphrase for “base-ubuntu-user” shared in the LastPass mentioned above in Pre-requisites step 1.

        ![ssh](files/ssh.png)

4. Perform the below command to apply CIS USG compliance

    ```bash
    make apply-usg-fixes
    ```

5. It installs and configures USG compliance and applies the changes to the Ubuntu 20.04 Pro machine. Then finally CIS audit report will be stored in the current directory(*~/dev-box/ansible/hardened-ubuntu-image/cis-report-files*). The previous command will take time to complete.
6. Check the report and ensure all the tests are passed

![report](files/report.png)

7. Reboot the EC2 instance
8. After that, Perform the below command to clean up the ec2 instance machine and take the AMI

    ```bash
    make create-cis-ami
    ```

9. Check the AWS console to verify the availability of “ID-Pal-CIS-hardened-ubuntu-AMI”
10. After crearting the AMI, perform the below command to delete the ubuntu-pro instance

    ```bash
    make delete-ubuntu-pro
    ```

### Reference links:

https://ubuntu.com/blog/cis-security-compliance-usg

https://bugs.launchpad.net/usg/+bug/2041840

https://www.tenable.com/audits/items/CIS_Ubuntu_20.04_LTS_v1.0.0_Server_L1.audit:a2c41d4f555a67bec7ad5c716baa9015

https://edu.anarcho-copy.org/GNU%20Linux%20-%20Unix-Like/Debian/CIS_Ubuntu_Linux_20.04_LTS_Benchmark_v1.1.0.pdf
