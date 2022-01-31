### Linux
```shell
ps -aux | grep <port> // 해당 port의 pid 확인
kill -9 <pid> // 해당 pid 킬
```

### Window
```shell
netstat -ano // 해당 port의 pid 확인
taskkill /f /pid <pid> // 해당 pid 킬
```
