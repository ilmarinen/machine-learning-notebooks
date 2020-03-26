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

4. From a different terminal, open an SSH terminal into the EC2 instance

```
ssh ubuntu@<ip-address-or-hostname> -NL 1234:localhost:1234
```

5. SSH into the EC2 instance and start Jupyter notebooks

```
jupyter notebook --no-browser --port 1234
```

(Cut and paste the login URL with token into your local browser, and you should
connect to the Notebook server.)


6. After working on your notebook a little and saving it, make sure to copy it to your local
repo and commit changes:

`scp ubuntu@<ec2-host-name>:~/machine-learning-notebooks/<notebook-name>.ipynb ./`
