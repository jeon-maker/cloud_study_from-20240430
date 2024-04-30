# 운영 기록

### 테라폼으로 EKS 버전 업그레이드

테라폼을 통해 eks의 instance type을 수정하고 apply를 하게되면

노드의 instance type을 변경할 수 있는데, 알아서 rolling upgrade 방식으로 작업을 수행해준다.

---

### ASG로 EKS node 증감하기?

ASG 설정으로 EKS node를 늘리거나 감소를 아무 준비 없이 하면 안된다.

Probe 설정을 해준 뒤에 해당 작업을 수행해야 한다.

Readiness probe가 설정이 안되어 있다면 Pod 가 준비 상태가 되기 전에 서비스 가능 상태로 인식하고 application을 띄우려고 하기 때문에 에러가 발생할 수 있다.
