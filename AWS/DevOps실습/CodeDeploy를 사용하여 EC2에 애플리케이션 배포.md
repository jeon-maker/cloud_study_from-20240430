실습 목표 :

이 실습에서는 실습 템플릿을 통해 이미 구성된 **2**개의 Amazon Elastic Compute Cloud(Amazon EC2) 인스턴스에 샘플 서비스 애플리케이션을 배포합니다. AWS CodeDeploy를 사용하여 소프트웨어를 Amazon EC2 인스턴스 플릿에 푸시하고 소프트웨어가 자동으로 배포, 등록, 시작되도록 합니다.

실행중인 EC2에 CodeDeploy 에이전트가 설치되어 실행 중인지 확인하기

https://www.notion.so/CodeDeploy-application-9b03f40f2ed849879fc1a840c3cfa8e3?pvs=4#0c8021f45b634732b9acd9b91fb2cb6b

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0af99f2e-8fd6-4b1d-b06a-d80ab9501941/4e227a88-360f-4ba0-bb52-6b05a9a9c446/Untitled.png)

EC2 인스턴스에 CodeDeploy 에이전트가 실행중임

Deploy 및 Deploy Group 생성 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0af99f2e-8fd6-4b1d-b06a-d80ab9501941/97e1a9f7-361a-4658-a4c5-f04f818ce02a/Untitled.png)

CodeDeploy에서는 배포 아티팩트를 S3 버킷에 어장해야 함.

CLI를 생성하여 버킷을 생성하자.

aws s3 mb s3://$bucketName 으로 버킷 생성 가능!

s3 버킷에 수정 버전을 푸시하고 정보를 CodeDeploy에 등록 

⇒ aws deploy push --application-name HeartBeatProduction-App --source HeartBeat-App --s3-location s3://$bucketName/HeartBeat-App.zip

생성한 s3 버킷의 애플리케이션 수정 버전을 EC2에 배포 

⇒ aws deploy create-deployment --application-name HeartBeatProduction-App --deployment-group-name HeartBeatProduction-App-Group --deployment-config-name CodeDeployDefault.AllAtOnce --description "Initial Deployment" --s3-location bucket=$bucketName,key=HeartBeat-App.zip,bundleType=zip

⇒ deployment가 생성이 됨

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0af99f2e-8fd6-4b1d-b06a-d80ab9501941/c87e6d1d-5f6f-41f9-88e8-b3cababc0f95/Untitled.png)

S3에 넣어져 있는 것을 배포하는듯?

디플로이먼트가 생성이 되었으며, 해당 인스턴스에 배포가 된 모습이다.

해당 인스턴스에서 S3에 올려놓은 어플리케이션이 실행이 되고 있는지 확인해보자.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0af99f2e-8fd6-4b1d-b06a-d80ab9501941/d8fc46fe-9bff-4159-b3e0-01c3c577e549/Untitled.png)

정상적으로 배포가 된 모습이다.

이번에는 변경 사항을 만들어 재배포를 해보자.

버킷에 업데이트 된 어플을 올리고,

aws deploy push --application-name HeartBeatProduction-App --source HeartBeat-App --s3-location s3://$bucketName/HeartBeat-App.zip

 디플로이먼트를 새로 생성하면 됨!

aws deploy create-deployment --application-name HeartBeatProduction-App --deployment-group-name HeartBeatProduction-App-Group --deployment-config-name CodeDeployDefault.AllAtOnce --description "Updated Deployment" --s3-location bucket=$bucketName,key=HeartBeat-App.zip,bundleType=zip

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/0af99f2e-8fd6-4b1d-b06a-d80ab9501941/8bd596f9-6b3a-4a9c-a805-0a5b623df75f/Untitled.png)
