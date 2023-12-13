# git-github-summary (code로 봐주세요)

# WD(working directory)-SA(staging area)-GR(git repository)

# 버전관리
:파일의 추가 밑 수정이력 관리

명령어 줄 인터페이스: Comnad Line Interface(CMD)
예시: Git Bash, Mac의 Terminal, Window의 CMD와 Powershell
그래픽 사용자 인터페이스: Graphic User Interface(GUI)

버전관리의 커밋:깃 저장소의 현상태를 저장
                
                지역저장소로 당기기(pull)
                     ----->
원격저장소(remote)--clone(복사)-> 지역저장소(Local Repository)
                    <------
                원격저장소로 밀기(push)

다양한 버전관리 시스템: CSV, SVN, Git Nercurial, Bazzar

저장 명령어: add, commit

Git이란? 분산버전관리 시스템/ 파일의 변경을 추적하는것에 사용되는 버전관리시스템
깃 사용의 장점: 지역시스템에 코드의 전체 사본 소유 가능
- 여러 개발자가 함깨 작업
- 변경사항 추적
- 분산버전 관리시스템 사용
- 여러개의 평행분기로 비선형개발을 지원

# 깃 내부 저장소
Working Directory--->Steaging Area--->Git Reposetory
+Stash

Github란? 
:버전관리를 위한 서버 저장소& 개발을 위한 협업관리 서비스(웹 호스팅)

# Git 명령어

$ git --version :버전확인
$ git config --list

ls: 리스트(현재폴더의 파일 표시)
pwd: 내가 지금 작업하고 있는 곳을 보여줘라

기본 편집기 설정
$ git config --설정범위/설정변수/설정 값
        [--system | --global | --local]
        => 모든 사용자 | 사용자의 모든 저장소 | 현재 저장소

기본설정

$ git config --global user.name [Username]
$ git config --global user.email [Email]
$ git config --global init.defaultBranch main

Warning 메세지 안뜨려면: $ git config --global core.safecrlf false
자동 줄바꿈: $ git config --global core.autocrlf true

$ git init : 현재폴더에 깃 리포지토리 생성
$ git init basic : 하위폴더에 basic 생성,깃 리포지토리 지정

$ cd fname : 파일로 이동
$ mkdir dname : 디렉토리 생성
$ touch fname : 빈 파일 생성
ex) touch a b c =>a,b,c 파일 생성

$ echo 문자열 : echo 뒤에 문자열 표시
$ cat fname : 파일 내용 보이기
$ cp a b : a를 b로 복사
$ mv f1 f2 :f1을 f2로 이름바꿈
$ rm fnaem : 파일 삭제
$ rm -rf dname : 디렉토리 삭제

ls 의 옵션
-ㅣ:파일 상세정보
- a :숨긴파일 표시
- t : 최신순 파일 정렬
- rt : 오래된순 파일 정렬
- f : 마지막 파일명 표시

cat 활용

$ cat f1 f2 | more : 내용을 페이지 처럼 보여준다
$ cat f1 f2 | head : 내용을 처음~10번째 줄만 출력한다
$ cat f1 f2 | tail : 내용을 끝에서 10번째 까지만 출력

> : 기존파일 지우고 저장
>> : 기존파일 뒤에 덧붙혀서 저장
< : 파일의 data를 명령에 입력

$ git status : 현재의 상태표시(붉-작업 디렉토리/녹-스테이징 영역)
$ git status -s : 간단히 표시

commit : 현재 steaging Area를 저장
$ git commit : 커밋 메세지를 입력
$ git commit -am : 메세지 입력 +add

$ git log : 로그 이력정보 표시
$ git log --oneline --graph --all : 한줄로 표시, 그림으로 표시, 전부표시

$ git show : 마지막 커밋의 정보 표시

# 버전이동

$ git checkout HEAD(~n) :  (이전)커밋으로 이동
$ git switch -d : 이전커밋으로 돌아오기

# 버전비교
$ git diff : SA에서 WR을 비교
$ git diff --staged : GR에서 SA를 비교
$ git diff HEAD : GR에서 WD를 비교

# 파일삭제

$ rm : 작업디렉토리 파일 삭제
$ git rm : WD&SA 파일 삭제
$ git rm -catched : SA파일 삭제

# 파일복원

$ git restore :SA의 파일을 WD로 복원
$ git restore --staged : GR의 파일을 SA로 복원
$ git restore --source=HEAD --staged --worktree : GR의 내용을 SA와 WD로 복구

# 명령별칭 생성

$ git config --global alias.별명 원래 명령어

# 버전
: 프로그램을 수정할떄 표시
SemVer: major,minor,patch 로 구성

#태그
:특정 커밋에 이름부여
- 주석태그 : 태그이름,작성자 이메일,태그시각 등
- 일반태그 : 태그이름만

# 브랜치
:일련의 파일 집합을 통채로 복사해서 독립적으로 다시 개발을 진행하는 개념
-> 병합은 merge
기본 브랜치 설정: $ git config --global init.defaultBranch bname

브랜치 생성
$ git branch bname : 브랜치 생성
$ git switch -c bname : 생성하고 HEAD로 이동
= $ git checkout -b bname

브랜치 확인
$ git branch,$ git branch -v

브랜치 이동
$ git switch bname
$ git checkout bname
$ git switch - :하나 돌아가기
$ git checkout - :하나 돌아가기




# clone(github,gitbuket 등)
:원격 저장소를  local repository에 복사
$git clone[복사주소][폴더이름] : 폴더이름 없으면 동일한 이름의 하부 폴더 생성

$ git remote: 원격 저장소 목록표시
$ git remote -v: 세부정보 표시
$ git remote show origin: 자세한 정보 표시
$ git remote rename origin org:origin을 org로 변경
$ git remote org: org 삭제

# push와 pull
push중 참조오류 ,인증오류 발생가능

push: 쓰기권한이 있어야 push가능(다른 사람의 저장소 일때 collaborator등록)
    : local 저장소의 코드변경 이력들이 원격저장소로 전송

$ git push <reponame> <bname>

pull=(git fetch+git merge) fetch와 merge를 순차적으로 진행
:fetch 원격저장소의 정보를 local repesitory로 가져오는 명령
:merge 변경된 정보를 local repository와 병합
$ git fetch origin ->$ git merge origin/main

# 오픈 소스 소프트웨어(oss)
-누구나 보고 코드를 사용할 수 있는 sw
OSI 인증마크 발행

oss의 시작
:free software: 리차드 스톨먼(GNU) | copyleft: 무료사용은 가능하지만 저작권 인정
  -> 발전되어 oss가 되었다

오픈소스지원 관리 서버: github, gitlab, bitbucket 등

oss의 장단점: 연구가 쉽다/품질보증, 보안이 어렵다

oss 개발모델:LAMP(Linux,Apache,MY SQL,PHP)
oss: python,sickit-learn,tensorflow,pythorch 등
os model: Android, Firefox, openoffice,git 등

os 라이센스 저작권

FOSS 라이센스(free): 반환의무/반환 불필요

(올라갈수록 제약성 강함 )
GPL
LGPL
Apache,BSD,Mit

# git 4영역 
# WD(working directory)-SA(staging area)-GR(git repository)-Stash(임시 저장소)

stash 영역: 작업 디렉토리와 SA의 내용을 커밋없이 저장(마지막 커밋내용)
->stack of git stash (last in-first out 방식)
in/push<--->out/pop

실행하면 GR->WD,SA // WD,SA->STASH        nothing to commit 상태가 된다

$ git stash [-m] : stash 영역으로 보내고 메세지 남기기
$ git stash save [name]: 명칭으로 저장

복원
$ git stash apply: WD만 복원
$ git stash apply --index: 둘 다 복원

목록            
$ git stash list-@stash{0}   -> 1번째
                -@stash{1}
                -@stash{2}

$ git stash show :stash 내용과 커밋내용의 차이를 표시
$ git stash show @stash{n}: 지정한 항목과 커밋 비교

$ git stash pop: stash 내용을 가져와 반영, 삭제

Untracked file 삭제
$ git clean :전부삭제
$ git clean -i:대화형 prompt표시
$ git clean -f: 무조건 삭제


# 브랜치 병합(merge)

1.fast-forward: 현재 브랜치가 병합할 브랜치의 뿌리인 경우 

a-B(뿌리)
  x-Y (y가 b의 브랜치 이력을 포함) 

2.3-way: 브랜치가 나뉘어져있어 병합
$ git merge bname[-m " "]

a-b-c-D-E
  x-Y----

$ git merge bname --no-ff[-m " "] : non fast forward 병합

a-B-------Z
    x-y----

* $ git merge --ff --only bname : ff만 진행시킨다!
* $ git merge squash bname: 커밋이력 넣지 않고 (+브랜치 이력) 모두 합해 병합,이후 커밋한다
  + 커밋 메세지 작성

# 병합충돌(conflict)
3-way 방식에서 병합시 파일이 다를때 발생

1(abc)-2(aBc)---------@@
-------a(abc)-b(ABC)----     @@에서 병합시, 파일이 다르다

해결방법: 파일을 수정하여 add와 commit을 해라

## 병합취소
:병합 이전 상태로 돌아감
$ git merge --abort
파일수정: 어떤 파일을 수정해 병합 할지 결정
$ code fname

## 브랜치 병합 rebase

3-way 상태에서의 base   a-B-c----d
B가 base이다              --x-y--

3-way 상태에서 선형적 통합이 이루어지게 된다
$ git rebase 를 한 후에 $ git merge 를 해야한다

rebase 충돌시
:파일 수정하여 $ git add를 하고, commit은 $ git rebase --continue 로 진행한다
+ $ git merge

merge와 rebase의 차이점: 이력의 차이(복잡/깔끔)
f-f merge와 rebase의 차이: 내리기와 따다 붙히기

다른 rebase 방법
$ git rebase [bname1] [bname2]: 1-2순으로 병합
+ $ git checkout bname1
+ $ git merge bname2


기본 편집기 설정
$ git config --global core.editor 'code--wait' (vs코드로 설정)

commit메세지 수정

$ git commit --amend : 코드창 열어 수정
$ git commit --amend -m " " :직접 입력해 수정
$ git commit --amend : 메세지 수정 없이 수정


rebase로 커밋 수정
:작업공간이 꺠끗할때 이전커밋 여러개 수정 가능

$ git rebase -i <HEAD~n> :HEAD~(n-1) 부터 수정가능

<rebase -i 명령어>
p(ick): 커밋수정 X ,그대로
r(eword): 개별 커밋 메세지 작성
s(qush): 계속된 이후(미래) 커밋을 이전(과거) 커밋에 변환(커밋이 뭉쳐짐)-> 커밋 메세지 입력
d(rop): 커밋삭제
pick D
pick CC -----------> CC에 EE,DD를 합친다
_________
sqush DD
s EE

# Reset
커밋 이력에서 이전커밋을 돌아감(roll back)
- 이력이 모두 사라짐, 깃 저장소는 이전 커밋 내용으로 돌아감
$ git reset [HEAD~n]

reset 옵션
$ git reset --hard [bname] :모든 공간에 복사(GR,SA,WD)
$ git reset --mixed [bname] :GR과 SA에만 복사
$ git reset --soft [bname] :GR에만 복사, 나머지는 그대로 남음

 + Reset 후 원래 상태로 되돌리기
$ git reset --hard ORIG_HEAD

checkout과 reset의 차이: checkout은 이력이 남고 HEAD만 바뀌지만 reset은 앞전 커밋이 지워진다

# 커밋취소 revert
:지정커밋을 취소해 이전 상태가 된다
 clean해야 가능,커밋 이력을 없애는 것이 아닌 새 커밋을 만들어 복원한다
 a-b-c  revert b->  a-b-c-b

 conflict 발생시
 파일수정->$ git add fname->$ git revert --continue

 $ git revert [HEAD~n] --no-edit : 이전 커밋 메세지 그대로 사용한다
















