# 깃허브 사용법 

### GitHub 시작하기

### 💡GitHub란 무엇인가요?

GitHub는 소프트웨어 개발 프로젝트를 위한 소스코드 관리 서비스입니다. GitHub를 사용하면 개인 포트폴리오를 올리고 관리할 수 있고 오픈 소스 프로젝트에도 효율적입니다.

<img width="1000" src="https://miro.medium.com/max/700/1*X9TKjhjwestOvFD0RsjoNQ.png">

### 기본 개념 파악하기

- 커밋 (commit) : 파일을 추가하거나 변경 내용을 저장소에 저장하는 작업
- 푸시 (push) : 파일을 추가하거나 변경 내용을 저장소에 업로드하는 작업
- 저장소 (repository) : 파일이나 디렉터리 등 소스코드를 저장하는 장소. 변경 이력을 관리하고자 하는 것들을 저장소의 관리하에 두어 변경 내역을 기록할 수 있다.
- Working Directory : 내가 작업하려는 PC 내의 디렉터리
- Staging Area : git commit하기전에 저장되는 git의 공간 (*커밋 예정인 파일, 디렉터리들이 모여있는 곳*)
- Local Repository : 내 PC에 파일이 저장되는 개인용 저장소
- Remote Repositroy : 원격 저장소 (*깃허브*)
- 브랜치 (branch) : 동시에 여러 버전을 관리할 수 있는 시스템

### 저장소에 업로드하기 (Push 하는 법 기본)

먼저 깃허브 메인 페이지에서 새로운 저장소를 만들고 진행하는 것이 좋습니다. 아래 과정은 저장소를 만든 직후 나타나는 화면(사진참조)에서도 확인할 수 있습니다.

<img width="1000" src="https://miro.medium.com/max/700/1*CmGMwOZIpTrPnTVw9W8GaQ.png">

1. 먼저 명령프롬프트 또는 터미널을 열어 저장소에 업로드할  파일이 있는 디렉터리로 이동합니다.
	 
	cd WorkingDirectory 주소
	
2. 깃허브를 처음 이용한다면 계정과 연동 해주어야합니다. 

    ```cmd
    git config --global user.name "닉네임"
    git config --global user.email "이메일"
    ```

3. 저장소 생성

    ```
     git init
    ```

4. 파일의 작성, 편집

5. 파일의 생성 / 변경/ 삭제를 git 인덱스에 추가

    ```
    git add 파일명(확장자포함) : 특정 파일을 Staging Area로 보냄
    
    git add * : 새로 생성한 모든 파일을 Staging Area로 보냄
    ```

6. 변경 결과를 로컬 저장소에 커밋 (git commit)

    ```
    git commit -m "커밋으로 기록할 내용 기입"
    ```

7. 로컬 저장소를 푸쉬해 원격 저장소에 반영 (git push)

    ```
    git push origin main
    ```

    


### 저장소에 업로드하기 (심화)

소스코드를 업로드하다보면 여러 버전을 동시에 관리해야하는 경우가 생길 수 있습니다. 방금 배운 업로드 방법으로 본다면 버전마다 다른 내용을 한 저장소에서 동시에 존재하도록 하기에는 어려움이 있습니다. 이럴 때 필요한 것이 branch입니다. 

- **branch의 생성과 이동, 삭제**

  현재 git에 기록된 branch 목록을 살펴보기 위해서는 다음과 같은 명령어가 필요합니다.

  ```
  git branch
  ```

  현재 브랜치에는 앞에 *이 붙어 사용중인 (git push 만 했을 때 default branch) 를 알 수 있습니다.

  - **branch의 생성**

    coin 이라는 이름의 branch 생성을 위해서는 다음과 같은 명령어가 필요합니다.

    ```
    git branch coin
    ```

  - **branch의 이동**

    branch를 생성했다면 해당 브랜치를 사용하기 위한 작업이 필요합니다. 아래 명령어는 coin 이라는 이름의 branch로 이동하도록합니다.

    ```
    git checkout coin
    ```

  - **또한 생성과 이동을 동시에 수행할 수도 있습니다**

    ```
    git checkout -b coin
    ```

  - **branch의 삭제**

    사용하지 않는 coin branch의 삭제를 위해서는 다음과 같은 명령어가 필요합니다.

    ```
    git branch -d coin
    ```

    

- **branch에 업로드하기 (push)**

  새로 만들어진 branch로 변경된 내용을 업로드 하기 위해서는 push의 branch를 지정해주면 됩니다.

  아래 명령어는 coin이라는 이름의 branch로 변경 내용을 푸쉬합니다.

  ```
  git push origin coin
  ```

  

- **branch에서 내려받기 (pull)**

  다른 사람이 새로 만들어진 coin branch의 소스코드로 개발하기 위해서는 어떻게 해야할까요. 

  아래의 명령어는 coin branch로 이동하여 전체 코드를 내려받거나 변경된 사항을 내려받는 것을 의미합니다.

  ```
  git checkout coin
  
  git pull
  ```

  

### 알아 두면 좋은 부록 명령어 📝

GitHub 홈페이지와 GitHub Desktop에서 일부 기능을 명령어 없이 간단한 클릭만으로 수행할 수 있지만 혼동하기 쉽고 제한적인 작업만을 수행할 수 있습니다. 그러므로 자주 사용하는 명령어들은 알아 두는 것이 좋습니다.

- **git status**

  저장소의 현재 상태를 확인하기 위해 사용합니다. 

  현재 브랜치의 이름과 추가,변경된 파일 및 디렉터리의 목록을 표시합니다.

  ```
  git status
  ```

  

- **git clone**

  원격 저장서의 내용을 로컬에 내려받아 관리하기 위해 사용합니다.

  오픈된 소스코드를 내려받을 때 자주 사용하는 방법이니 꼭 알아둡시다.

  ```
  git clone 저장소URL
  ```

  

- **git remote**

  원격 저장소를 조작하는 데 사용합니다.

  아래의 명령어는 coin branch로 이동하여 전체 코드를 내려받거나 변경된 사항을 내려받는 것을 의미합니다.

  ```
  git remote : 원격 저장소의 이름 목록을 표시
  
  git remote -v : 원격 저장소에 대한 자세한 목록 보기
  
  git remote add 저장소이름  저장소URL : 원격 저장소를 추가 
  
  git remote rm 저장소이름 : 원격 저장소를 제거
  ```

  

- **git reset**

  로컬 저장소에서 커밋을 취소하기 위해 사용합니다.

  사용하는 개발 툴의 log에서 해당 커밋을 undo하는 방법도 있습니다.

  ```
  git reset -soft HEAD ^ (가장 최근의 커밋을 되돌립니다.)
  ```

  
