### coreDNS란? 

coreDNS란 쿠버네티스에서 사용하는 DNS입니다. 

### coreDNS 자세히 살펴보기
`kubectl get po -n kube-system -l k8s-app=kube-dns` 명령어로 확인하면  coreDNS는 2개의 파드로 구성되어있다.
이 2두개의 파드에 대한 서비스는 kube-system 네임스페이스에서 kube-dns라는 이름으로 실행됩니다.

`kubectl get svc -n kube-system -l; k8s-app=kube-dns` 명령어로 kube-dns라는 서비스를 확인할 수 있다.
확인 결과 kube-dns는 TCP와 UDP모두 53포트를 사용하고 있습니다. 일반적으로 DNS는 53포트를 사용합니다.

`kubectl describe cm -n kube-system coredns` 명령어로 coreDNS의 coreFile정보를 확인할 수 있습니다.
(cm은 ConfigMap의 약자입니다.)