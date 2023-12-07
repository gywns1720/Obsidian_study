# Verdaccio
- NPM 개인 사설 저장소로 이용되며 

## 설치방법

### Docker 설치

```bash
# Docker Image 받기
docker pull verdaccio/verdaccio

# Docker Image Run
docker run -it -rm --name verdaccio -p 4873:4873 verdaccio/verdaccio
```

### NPM 설치
```bash
npm install -g verdaccio
```


## Verdaccio 사용하기

- shinopia 에서 사용 환경을 100% 지원하며 sinopia 의 환경 정보 및 파일 위치 파일명 등 동등하게 사용할 수 있다.
- shinopia 는 verdaccio 이전에 나왔던 NPM 개인 사설 저장소 이다. 2015년 유지보수가 끊겨 이걸 사용함.

### 사용자 가입 제한 
- npm adduser 는 원하는 사용자 등록을 가려내지 못합니다.
- max_users 로 사용자 가입을 제한 시킬 수 있다.
```yaml
# config.yaml
auth:
	htpasswd:
		file: ./htpsswd
		max_users: -1
```

### 알림
- npm publish 로 배포될 때마다 알림을 전송할 수 있다. 
```yaml
#config.yaml
notify:
	method: POST
	headers: [{'Content-Type' : 'application/json'}]
	endpoint: Slack Path
	content : '내용'
```

### 보안
- varaccio 4 부터 jwt 지원합니다.
```yaml
#config.yaml
security:
	api:
		legacy: true
		jwt:
			sign:
				expiresIn: 29d
			verify:
				someProps: [value]
		web:
			sign:
				expiresIn: 7d # 7d 기본값
			verify:
				someProps: [value]
# 혹은 SSL 인증서 또한 가능하다
https:
	key: ~/vardaccio-key.pem
	cert: ~/vardaccio-cert.pem
	ca: ~/vardaccio-csr.pem
```


## 패키지 배포
```bash
npm publish --registry http://172.30.1.24:4873/
```


### 패키지 삭제
```bash
npm unpublish <package_name> -f --registry http://172.30.1.24:4873/
```
