# AWS CloudFormation을 사용하여 기본 인프라 프로비저닝 및 관리

cloud 9을 이용하여 cloud formation 실습

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled.png)

cloud9을 사용하여 cloudformation 템플릿을 수정하고,  템플릿을 통해 cloudformation 스택을 생성합니다.

파라미터를 통해 스택을 생성 또는 업데이트할 때 템플릿에 사용자 지정 값을 입력할 수 있음.

파라미터 선언

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%201.png)

- 주의사항 : 여러 리소스를 명시할 경우,  바로 아래와 같은 나열 형태가 아닌
- ”  - “ 로 분류를 해줘야 함

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%202.png)

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%203.png)

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%204.png)

cli 를 통해 cloudformation로 인프라 프로비저닝 완료.

콘솔에서 확인해보자\

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%205.png)

### 

## CloudFormation 스택의 드리프트 탐지

방금 만든 stack의 Security Group을 수정하여 드리프트 보고서에서 식별이 되는지를 확인해보자

console에서 stack의 보안그룹을 수정한 뒤 stack의 detect drift 기능을 수행함 ⇒ view drift results 확인

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%206.png)

변경 내용을 자세히 보려면 view drift details

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%207.png)

위처럼 콘솔에서도 확인할 수 있고 아래와 같이 cli 상에서도 확인이 가능하다

![Untitled](AWS%20CloudFormation%E1%84%8B%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20%E1%84%80%E1%85%B5%E1%84%87%E1%85%A9%E1%86%AB%20%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%91%E1%85%B3%E1%84%85%E1%85%A1%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%202ee750799fea4866b9be8350ae39da0b/Untitled%208.png)

---

이번에는 콘솔상에서의 수정이 아닌 cli 위에서의 수정!

cli에서 수정을 하고 

aws cloudformation create-change-set --stack-name Lab1 --change-set-name Lab1ChangeSet --parameters ParameterKey=InstanceType,ParameterValue=t2.micro --template-body file://lab1-CS.yaml

와 같은 명령어를 수행하더라도 , 즉시 변경되는 것이 아니라 콘솔에서 최종적으로 변경을 수행해줘야 한다

---