### 우선순위
```text
Local > Global > System
```

### 설정
```shell
git config --system user.email "<email>"
git config --system user.name "<name>"
git config --global user.email "<email>"
git config --global user.name "<name>"
git config --local user.email "<email>"
git config --local user.name "<name>"
```

### 설정 확인
```shell
git config --system --list(-l)
git config --global --list(-l)
git config --local --list(-l)
git config --list(-l) // 전체 설정 확인
```
