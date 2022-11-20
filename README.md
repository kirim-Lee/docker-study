# 도커 컴포즈 설정 파일

- db, wordpress, nginx, nginx proxy 활용
- blog 로 접속시 워드프레스 연결
- 다른 로케이션은 사용자 페이지
- 다른 두 nginx와 wordpress는 db와 연결

## 워드 프레스 추가 설정

### docker-compose 로 컨테이너를 모두 올린 후에 추가적으로 해야할것

- 워드프레스 컨테이너에 접속

```console
docker exec -it wp /bin/bash
```

- blog로 폴더를 옮겼기 때문에 설정해야 하는 부분이다.
- 워드프레스가 자동으로 wp-config.php 를 만드는데 이건 blog에 생성되는 부분이 아님
- 따라서 wp-config.php 를 blog 폴더로 따로 카피 작업을 해줘야함

```console
 cp wp-config.php ./blog/
```

- 또한 wp-config.php 에 다음 구문을 추가 플러그인과 테마 설치를 바로 하겠다는 옵션

```php
  define('FS_METHOD', 'direct')
```

- 이제 localhost/blog 로 접속하면 워드프레스 설치를 할 수 있다.
