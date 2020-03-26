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

3. Run the Ansible playbook

`ansible-playbook setup-machine-learning-server.yaml -i hosts --user=ubuntu`

4. SSH into the EC2 instance and start Jupyter notebooks

```
jupyter notebook --no-browser --port 1234
```

5. From a different terminal, open an SSH terminal into the EC2 instance

```
ssh ubuntu@<ip-address-or-hostname> -NL 1234:localhost:1234
```