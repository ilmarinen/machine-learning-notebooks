# machine-learning-notebooks


1. Provision the GPU instance using the cloudformation script

```
aws cloudformation create-stack --stack-name <stack-name> --template-body file://provisioning/ec2-p2-xlarge.yml
```


2. Make sure your SSH key and SSH agent forwarding is enabled by adding the following lines to `~/.ssh/config`

```
Host <hostname> <host-ip>
    ForwardAgent yes
```

`ansible-playbook setup-database.yaml -i hosts --user=ilmarinen --extra-vars "ansible_sudo_pass=blacksmith database_password=<sidenoss-database-password>"`