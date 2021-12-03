base

- [chsasank/outline-wiki-docker-compose: Installation and docker compose to self host outline wiki: https://www.getoutline.com/](https://github.com/chsasank/outline-wiki-docker-compose)

```sh
git clone https://github.com/chsasank/outline-wiki-docker-compose
cd outline-wiki-docker-compose
make install
```

## Error

### minio가 실행되지 않는다. 계속죽어!

<table>
  <tr>
    <td>Old
    <td>New
  <tr>
    <td>MINIO_ACCESS_KEY
    <td>MINIO_ROOT_USER
  <tr>
    <td>MINIO_SECRET_KEY
    <td>MINIO_ROOT_PASSWORD
</table>

minio가 예전 버전의 이미지를 기준으로 환경변수를 만들어서 deprecated된 것들이 있다.
`docker logs`에 친절히 안내해줘서 알게되었다.
그래서 위처럼 새로운 환경변수로 넣어주고 실행한다.

### public data에 접근하지 못한다


현재 만들어진 minio는 버킷의 모든 path에 private하게 접근하는데 public한 접근도 필요하다

`.env.outline`
```
MINIO_BROWSER=on
```


<img width="1792" alt="스크린샷 2021-12-03 오후 6 42 39" src="https://user-images.githubusercontent.com/42893446/144581112-ce69d314-bf4a-4bf4-9685-f5244dad8b4c.png">

변경하고 웹 UI로 접속해서 해당 조건을 추가해준다.

그러면 설정, 유저의 프로필등등 모든 public한 데이터도 잘보여진다.

## 참고

- https://docs.min.io/docs/minio-docker-quickstart-guide.html
- https://github.com/chsasank/outline-wiki-docker-compose/issues/10#issuecomment-848697901