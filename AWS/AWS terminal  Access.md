# 권한 설정

-   ec2 생성시 만든 key파일의 권한을 변경한다.

```bash
sudo chmod 400 {key.pem}
```

# 접속

-   key파일과 인스턴스의 퍼블릭 IPv4 주소를 통해 접속한다.

```bash
ssh -i {key.pem}@ubuntu@{public IPv4 address}
```