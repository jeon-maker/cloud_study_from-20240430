## staticpod

본래 워커노드의 파드들은 마스터노드의 kube-api를 통해 통신을 하는데, 워커노드 자체에서 자체적으로 관리하는 파드.

staticpod는 워커노드마다 존재하는 kubelet이 자체적으로 관리하며, /etc/kubernetes/manifest 에 존재함

클러스터의 기능들을 할 수 있는 파드들을 staticpod로 주로 씀.
![image](https://github.com/jeon-maker/cloud_study_from-20240430/assets/77326600/daf5f805-27b0-4985-a268-23f1b4ce36fa)

이미지를 통해 static-pod 만들기

kubectl run —restart=Never —image=busybox static-busybox —dry-run=client -o yaml —command —sleep > /etc/kubernetes/manifests/static-busybox.yaml

컨트롤플레인에서 ssh (노드명) → 노드에 접속함
