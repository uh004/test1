# 6.9 원격 브랜치

🤝 깃은 다수의 개발자와 협업으로 코드를 유지할 수 있음

## 6.9.1 리모트 브랜치

💬 **리모트 브랜치**:원격 저장소에 생성한 브랜치 <br>
1. 원격 저장소와 로컬 저장소의 브랜치 이름을 보통 같지만 반드시 일치하지 않아도 가능하다. <br>
2. 리모트 브랜치는 보통 별칭/브랜치 이름 형태이다. <br>

## 6.9.2 실습 준비

### ⚡ 깃허브 실습 저장소에 New repository 클릭 후 새 저장소 생성
![실습1](https://user-images.githubusercontent.com/105197524/194878535-b499048e-8612-4f32-89ca-c6acb3a5f68a.png)

**새 저장소 생성 후 다음과 같이 실행**
```bash
$ git remote add origin 주소 ->원격 저장소 등록
$ git remote -v -> 원격 저장소 목록
```
![실습2](https://user-images.githubusercontent.com/105197524/194878543-353236e0-7cce-4fbe-a5cc-0de1a9d08af1.png)

## 6.9.3 브랜치 추적

## 🔭 브랜치 추적:원격 저장소 브랜치를 가리키는 것 다른 용어로 트래킹 브랜치 <br>
### 로컬 저장소는 마지막으로 연결된 리모트 브랜치의 커밋 해시 값을 항상 가지고 있음

## 6.9.4 브랜치 업로드

### ⚡ 등록된 원격 저장소의 리모트 브랜치는 remote show 명령어로 확인 가능
![실습3-1](https://user-images.githubusercontent.com/105197524/194880929-d806a7b2-ecdf-4933-bde6-2a66bfd3d5d0.png)

### ⚡ 로컬 저장소에서 main 브랜치를 전송하기
```bash
$ git push -u origin main -> main 브랜치 전송
$ git push -u origin hotfix -> hotfix 브랜치 전송
```
## 🔭 원격 저장소에 잘들어감
![실습4](https://user-images.githubusercontent.com/105197524/194878549-46a310ee-742a-4cad-a8d7-ef196bf9613d.png)


## 6.9.5 이름이 다른 브랜치

### ⚡  다른 개발자가 만든 원격 서버의 브랜치를 테스트하려고 할 때 자신의 브랜치 이름과 같으면 충돌이 발생한다.이때 브랜치를 직접 수동으로 지정할 때는 콜론(:)으로 구분한다.

```bash
$ git push -u origin feature:function -> 다른 이름으로 브랜치 전송
```
![실습5](https://user-images.githubusercontent.com/105197524/194878550-6bf29046-6bb4-423f-ac8a-0e7d23830521.png)

## 6.9.6 업스트림 트래킹

## 🔭 업스트림 트래킹:로컬 저장소의 브랜치와 원격 저장소의 브랜치를 업로드할 수 있도록 매칭되는 것

### ⚡ 새롭게 저장소를 복제
```bash
$ git clone https://github.com/uh004/gitstudy06.git gitstudy06_clone -> 복제
$ cd gitstudy06_clone -> 폴더 이동
$ git branch -v ->브랜치 목록
$ git branch -r -> 리모트 브랜치 목록
$ git branch -vv -> 트래킹 브랜치 목록
$ git checkout --track origin/function -> 업스트림 브랜치 생성
```
![실습6](https://user-images.githubusercontent.com/105197524/194878553-f06d0e18-c114-4191-a457-26c523e80a71.png)
```bash
$ code branch.htm -> 복제된 gitstudy06_clone의 function 브랜치를 수정합니다. 입력
```
### ⚡ 복제 저장소 -> 원격 저장소 push
![실습7](https://user-images.githubusercontent.com/105197524/194878557-d5f5bfbe-a10c-48e9-b324-27fceca75796.png)
### ⚡ 원격 저장소 -> 원본 저장소 pull
![실습8](https://user-images.githubusercontent.com/105197524/194878560-ab6656b5-db90-404b-b5cb-8505e1ac731c.png)


## 6.9.7 원격 브랜치 복사

### ⚡ 원격 저장소에 브랜치 aaa 생성
![제목 없음](https://user-images.githubusercontent.com/105197524/194883294-541e9504-ab48-4006-8de5-b347a2dc8ad6.png)
```bash
$ git fetch -> 브랜치 커밋 가져오기
$ git branch -r -> 원격 브랜치 확인
$ git checkout -b aaa origin/aaa -> 브랜치 생성 및 이동
$ code branch.htm -> 새로운 .... 작업을 합니다. 입력
$ git commit -am "testing aaa" -> 등록 및 커밋
$ git push -> 커밋 전송
```
![실습9](https://user-images.githubusercontent.com/105197524/194878561-d3c32b88-2821-4fb9-bd8c-0069ef283f6e.png)

## 6.9.8 업스트림 연결

### ⚡ 원격 저장소에 브랜치 bbb 생성
![실습10](https://user-images.githubusercontent.com/105197524/194878562-2e1f7ce0-7eb1-4614-9719-f3d0a01f6694.png)

```bash
$ git fetch ->서버의 브랜치 정보 갱신
$ git branch -r -> 원격 브랜치 목록
$ git checkout -b bug -> 브랜치 생성
$ git branch -vv -> 트래킹 브랜치 목록
$ git branch -u origin/bbb -> 업스트림 연결
$ git branch -vv ->트래킹 브랜치 목록
```
![실습11](https://user-images.githubusercontent.com/105197524/194878564-e8f425fb-0116-478c-827d-441ec0b363b1.png)

### 📄 로컬 저장소의 bug 브랜치가 원격 저장소에 있는 aaa 리모트 브랜치의 트래킹 브랜치로 업스트림 된것을 확인


