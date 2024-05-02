### Daemonset을 만드는 법

- Deployment yaml파일을 만든다

kubectl create deployment (이름)  - - image = (이미지)

-n (네임스페이스) - - dry-run=client -o yaml > ~~.yaml

PS. —dry-run=client는 서버에 변경 사항 적용 없이 어떤 결과가 미리 나올지 확인할 수 있는 옵션

Daemonset에는 

- replicas가 없다!
- strategy가 없다
- status 가 없다

yaml파일 적용 → kubectl apply -f ~~.yaml
