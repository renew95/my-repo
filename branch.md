# **브랜치(Branch)란?**

 브랜치란 독립적으로 어떤 작업을 진행하기 위한 개념입니다. 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에 여러 작업을 동시에 진행할 수 있습니다. 또한 이렇게 만들어진 브랜치는 다른 브랜치와 병합(Merge)함으로써, 작업한 내용을 다시 새로운 하나의 브랜치로 모을 수 있습니다.\

# **브랜치의 종류**

1. 통합 브랜치
   - 통합 브랜치란 어디든지 배포할 수 있는 버전을 만들 수 있어야 하는 브랜치입니다. 그렇기 떄문에 늘 안정적인 상태를 유지하는 것이 중요합니다. 여기서 '안정적인 상태'란 ''현재 작업 중인 프로그램의 모든 기능이 정상적으로 동작하는 상태''를 의미합니다.
   - 일반적으로 저장소를 처음 만들었을때 생기는 'master'브랜치를 통합 브랜치로 사용합니다.

2. 토픽 브랜치
   - 토픽 브랜치란, 기능 추가나  버그 수정과 같은 단위 작업을 위한 브랜치입니다. 여러 개의 작업을 동시에 진행할 때에는, 그 수 만큼 토픽 브랜치를 생성할 수 있습니다.
   - 토픽브랜치는 보통 통합 브랜치로부터 만들어 내며, 토픽 브랜치에서 특정 작업이 완료되면 다시 통합 브랜치에 병합하는 방식으로 진행되빈다. 이러한 토픽 브랜치는 '피처 브랜치'라고 부르기도 합니다.

<img src="C:\Users\dhkd4\Desktop\브랜치\슬라이드1.JPG" style="zoom: 50%;" />

#  **깃 브랜치 전략(Git-Branching strategy)**

프로젝트를 시작하면서 협업의 규모가 커지면 개인의 스타일대로 git을 사용하는 것이아닌 서로 규칙을 정하여 사용하게 됩니다. 이를 Git 브랜치 전략이라고 부릅니다. 

``` 
Branch 별 관한(Write, Read, Pull-Request)
Branch 생명주기 (짧게 유지하면서 명확하게)
Branch 를 통한 빠른 디버깅/스냅샷 확인

위 고려사항들은 모두 코드 품질 향상, 코드 가동성 향상을 목적으로 합니다. 그리고 버그가 발생하였을 때 해당 버전의 코드로 디버깅하여 원인을 찾고 상황 재현, 수정, 검증, 재패포까지의 단계를 체계적/ 안정적으로 처리할 수 있어야 합니다.
```

각 단계를 효과적으로 관리하기위해 Branch 전략 수립과 함께 Git 기능(hook, script 등)/솔루션(Github, GitLab, Gerrit, Stash, TFS 등)을 이용하여 자동화를 구상합니다.  자동화 구성은 코드 품질 향상을 위한 행동들을 팀 문화 혹은 절차로 대체할 수도 있습니다. 하지만 인간적인 측면과 신규 인력 투입 시 실수를 최소화 하는 역할로 ```자동화 구성과 제약```이 필요하다고 합니다.

처음 Branch전략을 수립하는 시점부터 '코드 품질, 코드 가독성(검색)'향상을 함께 목표로 설정하는데, 단순히 유명한 전략들을 따라하는게 아니고 현재 프로젝트 구성원, 회사의 제약 조건등을 고려해 '코드 저장관리'에서 최종 목표인 '코드 품질, 유지보수' 향상까지 제공하는 전략 수립을 수립할 수 있습니다.

# **Git flow(https://github.com/nvie/gitflow)**

 Vincent Driessen의 Git flow는 개발자가 더 큰 프로젝트에서 기능, 핫픽스 및 릴리스를 추적하는데 도움이 되는 git 분기 및 릴리스 관리 워크 플로입니다. 입력하고 기억해야할 많은 명령이 있어 더 쉽게 작업할 수 있도록 흐름의 일부를 자동화하는데 도움이 되는 도구(git-flow등)도 깔끔하게 만들어져 활용하기 좋습니다.

Git flow branch 전략 [참고1]

| Branch                 | 목적                  |
| :--------------------- | :-------------------- |
| master                 | 제품 출시             |
| develop                | 다음 버전 개발        |
| feature/[feature_name] | 기능 개발             |
| release                | 제품 출시 준비        |
| hotfix                 | 출시된 버전 버그 수정 |
|                        |                       |

Git-flow에는 [참고1]과 같은 5가지 종류의 브랜치가 존재합니다. 항상 유지되는 메인 브랜치들(master, develop)과 일정 기간동안만 유지되는 보조 브랜치들(feature, release, hotfix)이 있습니다.

[참고2] Git-flow 개발 흐름도

![ ](C:\Users\dhkd4\Desktop\git_flow.png)

### 1. **구조와 흐름**

- 가장 중심이 되는 브런치는 ```master```와 ```develop```브런치이며, 이 두 개 브런치는 무조건있어야 한다. 이름은 바뀔 수 있지만 거의 변경하지 않고 진행한다.
- 병합(merge)된 ```feature```, ```release```, ```hotfix``` 브런치는 삭제하도록 한다.

### 2. **장점**

- 명령어가 나와있다.
- 웬만한 에디터와 IDE에는 플러그인으로 존재한다.

### 3. **단점**

- 브런치가 많아 복잡하다.
- 안 쓰는 브런치가 있다. 그리고 몇몇 브런치는 애매한 포지션이다.



# **GitHub Flow**

Scott chacon이 Git flow가 GitHub에서 사용하기에 복잡하다 여겨 새롭게 만들어낸 관리 전략이다. 규칙과 흐름이 단순하다. master 브랜치에 대한 역할만 정확하다면 나머지 브랜치들은 관여하지 않는다. 그리고 pull request 기능을 사용하도록 권장한다. 

<img src="C:\Users\dhkd4\Desktop\Github_flow.png" style="zoom: 67%;" />

### **1. 특징**

- release 브런치가 명확하지 않은 시스템에서 사용에 맞게 되어있다.
- 여기에는 GitHub의 서비스 특성상. 릴리즈라는 개념이 없는 서비스를 진행하고 있어서 그런것으로 보임
- hotfix와 가장 작은 기능을 구분하지 않는다. 

### **2. 구조와 흐름**

1. master 브랜치는 어떤 때든 배포가 가능하다

   1.1 master 브랜치는 항상 최신의 상태이며, stable 상태로 배포되는 브런치이다. 그리고 이브런치에 대해서는 엄격한 role을 주어 사용한다.

2. 새로운 일을 시작하기 위해 브런치를 master에서 딴다면 이름은 어떤 일을 하는지 명확하게 작성한다.

   2.1 git-flow와 다르게 feature 브랜치나 develop 브랜치가 존재하지 않는다. 

   2.2 github 페이지에서 보면 어떤 일들이 진행되고 있는지 확인하기 쉽게 새로운 기능을 추가하거나 버그를 해결하기 위한 브랜치의 이름을 자세하게 어떤일을 하고있는지 작성해야한다.

3. 원격지 브랜치를 수시로 push 한다.

   3.1 git-flow와 가장 상반되는 방식이다. 항상 원격지에 자신이 하고 있는 일들을 올려 다른사람들도 확인할 수 있도록 해준다.

   3.2 이 방법의 좋은 점은 하드웨어에 문제가 발생하여 작업하던 부분이 없어지더라도 원격지에 있는 소스를 받아서 작업을 할 수 있도록 해준다.

4. 피드백이나 도움이 필요할 때, 그리고 머징 준비가 완료되었을 떄는 pull request를 생성한다.

   4.1 pull request는 코드 리뷰를 도와주는 시스템이다 이를 활용하여 자신의 코드를 공유하고 리뷰를 받을 수 있도록해야한다.

5. 기능에 대한 리뷰와 사인이 끝난 후 master로 병합(merge)한다.

6. master로 병합되고 푸시되었을떄는 즉시 배포되어야 한다.

   GitHub Flow의 핵심인듯한 master로 머지가 일어나면 hubot을 이용하여 자동으로 배포가 되도록 설정해 놓는다.

### **3. 장점**

- 브런치 전략이 단순하다.
- 처음 git을 접하는 사람에게 정말 좋은 시스템이 된다.
- github 사이트에서 제공하는 기능을 모두 사용하여 작업을 진행한다.
- 코드 리뷰를 자연스럽게 사용할 수 있다.
- CI가 필수적이며, 배포는 자동으로 진행할 수 있다.
- Github가 작업을 할 때 이렇게 작업하고 있다.

### **4. 단점**

- CI와 배포 자동화가 되어있지 않은 시스템에서는 사람이 관련된 업무를 진행한다.
- 많은 것들이 올라오기 시작하면 어려워진다.

# **GitLab Flow**

Github에서 말하는 flow는 너무나도 간단하여 배포, 환경 구성, 릴리즈, 통합에 대한 이슈가 많았다 그것을 보완하기 위해 GitLab에서 관련 내용들을 추가적으로 덧붙여 설명한 것

![](C:\Users\dhkd4\Desktop\gitlab_flow.png)

- Merge/pull requests with GitLabflow
- issues with GitLab flow

### **참고(https://ujuc.github.io/2015/12/16/git-flow-github-flow-gitlab-flow/)**







# **참고자료(Reference)**

git-flow 설명(By [Jeff Kreeftmeijer](https://jeffkreeftmeijer.com/)) : https://jeffkreeftmeijer.com/git-flow/

git-flow 설명(우아한형제들) : https://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html

*Git-flow, Github-flow, GitLab-flow에 대한 소개 : https://ujuc.github.io/2015/12/16/git-flow-github-flow-gitlab-flow/

Git 브랜칭 전략 : Git-flow와 Github-flow : https://hellowoori.tistory.com/56

GitHub-flow 전문 : https://scottchacon.com/2011/08/31/github-flow.html

GitHub-flow 흐름 이해 : https://guides.github.com/introduction/flow/

GitLab-flow 에 대한 내용: https://docs.gitlab.com/ee/topics/gitlab_flow.html