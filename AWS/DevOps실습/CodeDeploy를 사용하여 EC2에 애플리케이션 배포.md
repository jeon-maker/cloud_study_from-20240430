실습 목표 :

이 실습에서는 실습 템플릿을 통해 이미 구성된 **2**개의 Amazon Elastic Compute Cloud(Amazon EC2) 인스턴스에 샘플 서비스 애플리케이션을 배포합니다. AWS CodeDeploy를 사용하여 소프트웨어를 Amazon EC2 인스턴스 플릿에 푸시하고 소프트웨어가 자동으로 배포, 등록, 시작되도록 합니다.

실행중인 EC2에 CodeDeploy 에이전트가 설치되어 실행 중인지 확인하기

![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/24d69c0f-696f-4ffd-b9e0-37b47715a4cf)

![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/9182a9fe-07e0-41b5-82a3-bc1288b60212)



EC2 인스턴스에 CodeDeploy 에이전트가 실행중임

Deploy 및 Deploy Group 생성 

![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/7e4db30f-3397-4b73-b67e-5392c2d53de1)

CodeDeploy에서는 배포 아티팩트를 S3 버킷에 어장해야 함.

CLI를 생성하여 버킷을 생성하자.

aws s3 mb s3://$bucketName 으로 버킷 생성 가능!

s3 버킷에 수정 버전을 푸시하고 정보를 CodeDeploy에 등록 

⇒ aws deploy push --application-name HeartBeatProduction-App --source HeartBeat-App --s3-location s3://$bucketName/HeartBeat-App.zip

생성한 s3 버킷의 애플리케이션 수정 버전을 EC2에 배포 

⇒ aws deploy create-deployment --application-name HeartBeatProduction-App --deployment-group-name HeartBeatProduction-App-Group --deployment-config-name CodeDeployDefault.AllAtOnce --description "Initial Deployment" --s3-location bucket=$bucketName,key=HeartBeat-App.zip,bundleType=zip

⇒ deployment가 생성이 됨

![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/aa44525f-5453-444a-9175-1bace827cdde)
S3에 넣어져 있는 것을 배포하는듯?

디플로이먼트가 생성이 되었으며, 해당 인스턴스에 배포가 된 모습이다.

해당 인스턴스에서 S3에 올려놓은 어플리케이션이 실행이 되고 있는지 확인해보자.

![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/513d5ec8-ee3f-4a83-8bee-758b3c149050)

정상적으로 배포가 된 모습이다.

이번에는 변경 사항을 만들어 재배포를 해보자.

버킷에 업데이트 된 어플을 올리고,

aws deploy push --application-name HeartBeatProduction-App --source HeartBeat-App --s3-location s3://$bucketName/HeartBeat-App.zip

 디플로이먼트를 새로 생성하면 됨!

aws deploy create-deployment --application-name HeartBeatProduction-App --deployment-group-name HeartBeatProduction-App-Group --deployment-config-name CodeDeployDefault.AllAtOnce --description "Updated Deployment" --s3-location bucket=$bucketName,key=HeartBeat-App.zip,bundleType=zip
![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/3dde9c6e-9d01-47aa-afe8-06f42d0da390)
