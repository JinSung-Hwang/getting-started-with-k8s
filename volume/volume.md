## 볼륨(volume)이란?
어플리케이션의 데이터를 보관하는 저장소를 볼륨(volume)이라고 함

### stateful이란?
데이터를 저장소에 저장해두는 애플리케이션을 stateful하다고 함

### stateless이란?
어떤 데이터도 저장소에 저장해두는 않는 애플리케이션을 stateless하다고 함

## volume 사용 이유
데이터를 컨테이너에 저장해둔다면 컨테이너가 재시작되면 데이터는 모두 사라지게 됨
재시작해서도 데이터를 보존하려면 볼륨을 이용해야함
즉, stateful 애플리케이션 운영을 위해서 필요함

## volume의 종류
임시 볼륨: 파드 내의 공간에 볼륨을 생성하여 데이터를 저장함, 파드가 없어지면 볼륨과 데이터들도 없어짐
로컬 볼륨: 워커 노드내의 디스크 저장소에 데이터를 저장함, 워커 노드가 사라지면 볼륨과 데이터들도 없어짐
외부 볼륨, 영구 볼륨: 노드의 외부에 있는 저장소에 데이터를 저장함, 파드와 워커 노드의 라이플 사이클에 영향을 받지 않음, 다만 추가적인 저장소 비용이 발샘함

## 외부 볼륨, 영구 볼륨(persistent volume) 사용법
영구 볼륨을 사용하려면 3~4가지 파일이 필요하다.
  1. PersistentVolume: 데이터를 영구적으로 보관할 수 있는 볼륨 - 예시) persistent-volume.yaml 참조
  2. PersistentVolumeClaim: 볼륨을 요청하는 볼륨 클레임, [어탭터 패턴 처럼 사용되는 오브젝트 인듯하다] - 예시) persistent-volume-claim.yaml 참조
  3. pvc-deployment: 영구 볼륨을 사용할 deployment 오브젝트, PersistentVolumeClaim을 연결한다. - 예시) pvc-deployment.yaml 참조
  4. service: deployment에 필요에 따라 파드를 외부로 노출 시킬 service - 예시) mysql-service.yaml 참조
