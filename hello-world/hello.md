# hello git

## git 기초 명령어 요약

- clone : 원격 저장소 복사(=git 원격 저장소와 소스트리를 연결해주는 작업)
- add : 스테이지 영역에 작업 파일 추가
- commit : 세이브, 스테이지 영역의 파일들을 가지고 커밋(=세이브)를 만들 수 있다.
- push : 원격 저장소에 커밋을 업로드한다.

## 파일의 내용 되돌리기

- 특정 파일의 내용을 마지막 커밋으로 돌리고 싶다면 해당 파일 선택 후 '코드 뭉치 버리기' 선택

## 소스트리 패스워드 인증을 잘못할 경우

- 소스트리 패스워드 인증은 무조건 토큰으로 해야한다! git 비밀번호를 입력하거나 잘못입력했을 경우 막혀버린다.
- C:\Users\[계정이름]\AppData\Local\Atlassian\SourceTree
의 경로를 통해 들어가 passwd 파일을 삭제해주어야한다. 
- 계정이름은 각자의 컴퓨터 계정이름이다. 나같은경우 User.

## credential helper selector

- 초기 설정이 되어있지않다면 pull/push시마다  credential helper selector 창이 뜰 수 있다.
- 이때 주요하게 알아둘 것은 cache / store 정도
- cache 모드는 일정시간동안 메모리에 사용자 이름과 암호 같은 인증정보를 기억한다. 이는 디스크에 저장되지않고 메모리에서도 15분만 유효하다.(보안성 높음)
- store 모드는 디스크에 텍스트 파일로 저장하며 계속 유지한다. 리모트의 인증정보를 변경하지 않는 한 다시 인증정보를 입력하지 않아도 된다.
- 이 외에 몇가지 모드가 더 있지만 정확히 어떤 역할을 하는지 알지는 못한다.
- 재설정을 어떻게 하는지도 찾아볼 것!(현재 내 컴퓨터 cache 상태)

## 브랜치 변경하기

- 브랜치란: 기존 내용을 유지한 채 새로운 내용을 추가하고 싶을 때 사용한다.
- 체크아웃 :  특정 브랜치(혹은 커밋)으로 돌아가고 싶을 때 사용
- 소스트리의 체크아웃 : 브랜치 이름을 더블 클릭하는 것만으로 체크아웃 가능
- 일반적으로는 브랜치에서 작업, 마스터에 최종내용을 넣어야한다. 

## 병합하기 1

- 헤드 브랜치에 변경사항이 없고 
- 병합 대상 브랜치가 헤드로부터 시작된 경우
- 아주 쉽게 병합 가능 = Fast-forward

## 병합하기 2

- 헤드 브랜치에 추가적인 커밋이 생기는 경우
- 진짜 병합이 필요해 진다.
- 충돌이 안 나면 좋은데, 충돌이 나도 겁내지 말자.

## 충돌 해결하기

- 제일 중요한 점 : 겁내지 말아요!
- 같은 파일을 병합 대상 두 커밋에서 동시 수정했을 경우 충돌이 날 확률이 높다!
- 에디터 사용, 혹은 SourceTree를 사용해서 충돌 해결 가능하다.

## 커밋 되돌리기

### reset 사용하기

- 장점 : 쉽다.
- 단점 : 커밋이 날아간다. 그리고 강제 푸시가 필요하다.

### branch 만들어서 되돌리기 (★)

- 장접 : 쉽다. reset과 달리 내용이 사라지지않는다.
- 단점 : 트리가 지저분해진다.

## revert

- 역시 커밋이 없어지지 않는다.
- 장점 : 가장 정석적
- 단점 : 충돌이 날 수 있다.

## revert 2

- revert로 여러 커밋을 되돌리려면 최신부터 순서대로 revert 하자
- 그렇게 하면 충돌을 막을 수 있다.

## 커밋 덮어쓰기

- 필요하다면 이전 커밋 덮어쓰기도 가능
- 'commit --amend'
- 이미 push를 한 경우 'push --force'가 필요함

## stash

- 다른 브랜치로 체크아웃하기 전에 편재 작업내용을 저장하는 임시 저장소
- 유용하니 잘 사용하자.

## 이것도 넣고싶다.

- 여러 브랜치를 최종적으로 메인(마스터)에 병합할 때에는 충돌이 날수도 있고 안날 수도 있다. 나면 겁내지말고 차근차근 따지면 된다!
- 어차피 여러가지를 동시에 진행중이라 여러 파일을 각자 만들고 있는거라면 공용파일에 연결하는 부분에서만 충돌이 날 것!

## rebase

- merge 처럼 두 브랜치를 합칠 때 사용.
- 현재 브랜치가 대상 브랜치 위로 올라감!
- 위험하니 조심스레 사용 필요 (특히 협업!)

## 기타 주의 사항

- 코드를 남기려고 주석을 달지 말자.
- 커밋 메시지를 잘 쓰자.
- 한가지 구현이 완료될 때마다 커밋을 하자. (자주하자!)
