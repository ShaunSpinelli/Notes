#




## Connectiong to EC2 Instance

Run from fast ai folder where pem file is stored

```bash
$ ssh -i your-aws-key-pair-filename.pem -L 9999:127.0.0.1:8888 ubuntu@ec2-34-216-178-210.us-west-2.compute.amazonaws.com
```
note if there is an error for unsecured pem file
run 
```bash
$ chmod 400 your-aws-key-pair-filename.pem
```

### Should now be connect to EC2 Instance

## Openning Jupyter Note Book on AWS

Activate python environemnt

```bash
$ source activate python3
```

```bash
$ jupyter notebook
```

Copy url and change localhost to 9999 when you paste it in the browser

-L 9999:127.0.0.1:8888