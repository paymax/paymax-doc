## 生成RSA公私钥
###	Linux用户(以Mac为例)
* 生成RSA私钥：
  ```shell
  #在Terminal中输入下面命令（该命令会生成1024位的私钥）：
  openssl genrsa -out rsa_private_key.pem 1024
  #回车后如下显示：
  Generating RSA private key, 1024 bit long modulus
  ...++++++
  ........++++++
  e is 65537 (0x10001)
  #此时你可以在当前目录下看到rsa_private_key.pem文件了
  ```

* 把RSA私钥转换成PKCS8格式【注意：对于使用Java的开发者，将pkcs8在console中输出的私钥去除头尾、换行和空格，作为开发者私钥，对于.NET和PHP的开发者来说，无需进行pkcs8命令行操作。】
  ```shell
  #在Terminal中输入下面命令：
  openssl pkcs8 -topk8 -inform PEM -in rsa_private_key.pem -outform PEM -nocrypt -out rsa_private_key_pkcs8.pem
  #回车后生成PKCS8格式的私钥(rsa_private_key_pkcs8.pem)。
  ```

* 生成公钥【注意：往 Paymax 保存商户公钥时，需要去除公钥内容的**头尾、换行和空格**】：
  ```shell
  #在Terminal中输入下面命令：
  openssl rsa -in rsa_private_key.pem -out rsa_public_key.pem -pubout 
  #回车后如下所示：
  writing RSA key
  #此时你可以看到一个文件名为rsa_public_key.pem的文件，这个就是公钥。
  ```

### Windows用户
* 下载openssl工具 [openssl tools](http://pan.baidu.com/s/1eS7FbKA)
* 安装好后,打开openssl的命令行工具，执行下面命令：
  ```shell
  #生成RSA私钥
  genrsa -out rsa_private_key.pem   1024
  #RSA私钥转换成PKCS8格式【注意：对于使用Java的开发者，将pkcs8在console中输出的私钥去除头尾、换行和空格，作为开发者私钥，对于.NET和PHP的开发者来说，无需进行pkcs8命令行操作。】
  pkcs8 -topk8 -inform PEM -in rsa_private_key.pem -outform PEM -nocrypt -out rsa_private_key_pkcs8.pem
  #生成RSA公钥【注意：往 Paymax 保存商户公钥时，需要去除公钥内容的头尾、换行和空格】：
  rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem
  ```

* 成功生成RSA公私钥。

### RSA样例
* 标准格式的RSA私钥
  ```
  -----BEGIN RSA PRIVATE KEY-----
  MIICXAIBAAKBgQDSlOqMbkBq+uv2grR1qGjkTBtOB4EVnfLLYCaEXiWD3qezvb1V
  N2nV9GsUxtbPc33azcXoQI9YKmbyj2GL5rgHVs00xcVjQ6TmRLJ+dhKqaWJtIoFv
  oI4E3SplopmuX+xegD0xj9bLIVMQ3LclZuoklF7Xtf9zNsjqpPyJ6f/y+wIDAQAB
  AoGATYVgqv3TXQ6uWvtW75Flu9WAn8MHdCvHO7NTuprl+Ju45OROlNZnccoeuXFR
  luEPTcM+vfc2TeCeMWEzKctvpykFPWcl/mMT4MReJTRPWEUM385vF7utpOasxyze
  pFaANtnra8fT2TSZMwjrZndIS8YfQKW6vWqo1wwKmVCjyEECQQDsaGVYyf9f6wbu
  D9aGwFQ2zKrYCAcAfjd9ZoNGlc9+sbe2QQYXvCjmJ3QT0dVi7pxOsDJj5RBZ10up
  Km0NY84xAkEA5AiYtiPt0hZ8jDt1VkNpW1cU32veCbYHAmnR6osgVljWAaBCx18w
  1nJkNLLPmDA3EpyDnCGyEdN9MGQlyHVs6wJAJDPIcVRdmx6urP4X6ALD4rBs6TAx
  gk3RyY5NRB3k7I3iiDJk8HWL/dLE39QeTUwk+5fX35xQaLGjkIBCuu4xwQJBAKRc
  Ad4+lVr49DqLXK6ZliXM5XGIKRksx26Y4UHBl8RE8bNoVNmpJeVbvBgzzedu0TMr
  9ryhmNy6aCBp/sW2xZMCQAfiwO3orq/d8RxoM/g/rPd9ZlmW/mMuNLrJ/cmxrLW9
  rbv4TmuVL4l/AKCdK0J8VzgVMsoN+snsL4y4rHgcakI=
  -----END RSA PRIVATE KEY-----
  ```
* PKCS8格式的RSA私钥
  ```
  -----BEGIN PRIVATE KEY-----
  MIICdgIBADANBgkqhkiG9w0BAQEFAASCAmAwggJcAgEAAoGBANKU6oxuQGr66/aC
  tHWoaORMG04HgRWd8stgJoReJYPep7O9vVU3adX0axTG1s9zfdrNxehAj1gqZvKP
  YYvmuAdWzTTFxWNDpOZEsn52EqppYm0igW+gjgTdKmWima5f7F6APTGP1sshUxDc
  tyVm6iSUXte1/3M2yOqk/Inp//L7AgMBAAECgYBNhWCq/dNdDq5a+1bvkWW71YCf
  wwd0K8c7s1O6muX4m7jk5E6U1mdxyh65cVGW4Q9Nwz699zZN4J4xYTMpy2+nKQU9
  ZyX+YxPgxF4lNE9YRQzfzm8Xu62k5qzHLN6kVoA22etrx9PZNJkzCOtmd0hLxh9A
  pbq9aqjXDAqZUKPIQQJBAOxoZVjJ/1/rBu4P1obAVDbMqtgIBwB+N31mg0aVz36x
  t7ZBBhe8KOYndBPR1WLunE6wMmPlEFnXS6kqbQ1jzjECQQDkCJi2I+3SFnyMO3VW
  Q2lbVxTfa94JtgcCadHqiyBWWNYBoELHXzDWcmQ0ss+YMDcSnIOcIbIR030wZCXI
  dWzrAkAkM8hxVF2bHq6s/hfoAsPisGzpMDGCTdHJjk1EHeTsjeKIMmTwdYv90sTf
  1B5NTCT7l9ffnFBosaOQgEK67jHBAkEApFwB3j6VWvj0OotcrpmWJczlcYgpGSzH
  bpjhQcGXxETxs2hU2akl5Vu8GDPN527RMyv2vKGY3LpoIGn+xbbFkwJAB+LA7eiu
  r93xHGgz+D+s931mWZb+Yy40usn9ybGstb2tu/hOa5UviX8AoJ0rQnxXOBUyyg36
  yewvjLiseBxqQg==
  -----END PRIVATE KEY-----
  ```

* RSA公钥
  ```
  -----BEGIN PUBLIC KEY-----
  MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDSlOqMbkBq+uv2grR1qGjkTBtO
  B4EVnfLLYCaEXiWD3qezvb1VN2nV9GsUxtbPc33azcXoQI9YKmbyj2GL5rgHVs00
  xcVjQ6TmRLJ+dhKqaWJtIoFvoI4E3SplopmuX+xegD0xj9bLIVMQ3LclZuoklF7X
  tf9zNsjqpPyJ6f/y+wIDAQAB
  -----END PUBLIC KEY-----
  ```