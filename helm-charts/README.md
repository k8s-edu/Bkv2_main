# '컨테이너 인프라 환경 구축을 위한 쿠버네티스/도커' 헬름 차트 저장소

![img1](https://img.shields.io/badge/helm-3.x+%20-blue)
![img3](https://img.shields.io/badge/license-Apache%202-blue)

🧰 제공하는 차트는 다음과 같습니다.


- MetalLB
- Jenkins
- nfs-subdir-external-provisioner
- prometheus
- grafana

## 헬름 설치하기
헬름 설치는 [공식 문서](https://helm.sh/docs/intro/install/)를 참조하여 설치합니다.


## 헬름 차트 저장소 등록하기

```bash
$ helm repo add edu-k8s https://k8s-edu.github.io/Bkv2_main/helm-charts/
$ helm repo update
```
