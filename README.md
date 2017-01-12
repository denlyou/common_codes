:octocat: [denlyou/common_codes](https://github.com/denlyou/common_codes)
# 코드집

#### LIST
- MariaDB (MySQL)
- Linux
- Node.js
- jQuery
- Laravel
- GIT
- Firebase
- php

## MariaDB with SQL

- [트렌잭션](https://mariadb.com/kb/en/mariadb/start-transaction/)

```sql
SET autocommit=0;
START TRANSACTION;
COMMIT;
ROLLBACK;
SET autocommit=1;
```

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

### Advance
- 시간 필드 기준으로 10분단위로 그룹

```sql
SELECT *, MAX(`datetime`) as _alias
  FROM 테이블명
 WHERE 1
GROUP BY MONTH( datetime ) , DAYOFMONTH( datetime ) , HOUR( datetime ) , FLOOR( MINUTE( datetime ) /10 )
ORDER BY _dt DESC ;
```

- Replication (서버 복제)

### Trouble Shootings
- 관리자 패스워드를 잊어먹었을 때
- mysqldump


## Node.js
- (예정)

## jQuery + js
- `$.ajax`

```js
$.ajax({ type: "POST", dataType: "json",
  url: "/search_ajax_jobs.php",
  data: { 'jobs': _jobs },
  success: function(data){
    // TODO
  }
});
```
** 보내는 쪽도 header가 확실히 json 타입이어야 함 **

- `$.post`, `$.get`은 IE8~9에서 안됨 ㅠㅠ
- 또 IE9이하 forEach 미지원...
- 시간관련 좋은 라이브러리
  - momentjs (http://momentjs.com/)
- ajax 크로스 도메인 ie8/9 문제 :  https://github.com/MoonScript/jQuery-ajaxTransport-XDomainRequest

### plug-in's


## firebase
- 4web
- 4ios

## git CLI

- (git 콘솔 명령어)

```git
git init
git remote -v
```

## php

- header

```php
<?php
// 캐릭터셋 UTF8
header("Content-Type : text/html; charset=UTF-8");
// 리다이렉트
header('Location: http://www.example.com/');
// response code 보내기
header("HTTP/1.0 404 Not Found");
// pdf파일로 example
header("Content-type : application/pdf");
header('Content-Disposition : attachment; filename="downloaded.pdf"');
readfile('original.pdf');
?>
```

- mysqli db connection

```php
<?php

$mysqli = new mysqli("localhost", "SimpleFeedback", "SimpleFeedback", "SimpleFeedback");
if ($mysqli->connect_errno) {
    die("Failed to connect to MySQL: (" . $mysqli->connect_errno . ") " . $mysqli->connect_error);
}
$mysqli->query("SET NAMES utf8");

?>
```

- session example

```php
<?php
  // Get the private context
  session_name('Private');
  session_start();
  $private_id = session_id();
  $b = $_SESSION['pr_key'];
  session_write_close();

  // Get the global context
  session_name('Global');
  session_id('TEST');
  session_start();

  $a = $_SESSION['key'];
  session_write_close();
?>
  <html>
    <body>
      <h1>Test 2: Global Count is: <?=++$a?></h1>
      <h1>Test 2: Your Count is: <?=++$b?></h1>
      <h1>Private ID is <?=$private_id?></h1>
      <h1>Gloabl ID is <?=session_id()?></h1>
      <pre>
      <?php print_r($_SESSION); ?>
      </pre>
    </body>
  </html>

<?php
  // Store it back
  session_name('Private');
  session_id($private_id);
  session_start();
  $_SESSION['pr_key'] = $b;
  session_write_close();

  session_name('Global');
  session_id('TEST');
  session_start();
  $_SESSION['key']=$a;
  session_write_close();
?>
```
