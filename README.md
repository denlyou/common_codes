:octocat: [denlyou/common_codes](https://github.com/denlyou/common_codes)
# 코드집

#### LIST
- MariaDB (MySQL)
- Linux
- nodejs
- jQuery
- Laravel
-

## MariaDB with SQL
- 새로운 유저 생성
`CREATE USER '유저명'@'접속허용범위' IDENTIFIED BY '패스워드';`
- 테이블 관리 권한
`GRANT all privileges ON DB명.테이블명 TO '유저명'@'접속허용범위' IDENTIFIED BY '패스워드';`
- 변경사항 저장
`flush privileges;`

```sql
create user 'userid'@'%' identified by 'password';
grant all privileges on dbname.* to 'userid'@'%' identified by 'password';
flush privileges;  
```

#### Advance
- 시간 필드 기준으로 10분단위로 그룹

```sql

```

#### Trouble Shootings
- 관리자 패스워드를 잊어먹었을 때

## Node.js
- (예정)

## jQuery
- ajax

#### plug-in's


## firebase
- 4web
- 4ios


## git CLI
- (git 콘솔 명령어)
