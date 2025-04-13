# Ansible을 이용한 Kubernetes 클러스터 구축

이 프로젝트는 Ansible과 Kubeadm을 사용하여 Kubernetes 클러스터를 자동으로 구축하는 프로젝트입니다.

## 프로젝트 구조

```
.
├── ansible/
│   ├── inventory/
│   │   ├── hosts.yml
│   │   └── group_vars/
│   │       ├── all.yml
│   │       ├── masters.yml
│   │       └── workers.yml
│   ├── playbooks/
│   │   ├── prerequisites.yml
│   │   ├── kubeadm-setup.yml
│   │   ├── network-setup.yml
│   │   └── addons.yml
│   └── roles/
│       ├── common/
│       ├── kubernetes/
│       └── calico/
├── kubernetes/
│   └── manifests/
└── docs/
    ├── architecture.md
    └── troubleshooting.md
```

## 구성 요소

### 핵심 인프라
- Kubernetes (kubeadm)
- Calico CNI
- CoreDNS
- Metrics Server

## 사전 요구사항
- Ubuntu 20.04 이상
- Ansible 2.9 이상
- Python 3.8 이상
- 최소 2개의 노드 (1개의 마스터, 1개의 워커)
- 최소 하드웨어 요구사항:
  - 마스터 노드: 4 CPU, 8GB RAM, 50GB 스토리지
  - 워커 노드: 4 CPU, 8GB RAM, 50GB 스토리지

```bash
ansible-playbook -i ansible/inventory/hosts.yml ansible/playbooks/prerequisites.yml
ansible-playbook -i ansible/inventory/hosts.yml ansible/playbooks/kubeadm-setup.yml
ansible-playbook -i ansible/inventory/hosts.yml ansible/playbooks/network-setup.yml
ansible-playbook -i ansible/inventory/hosts.yml ansible/playbooks/addons.yml
```

## 설정
모든 설정 파일은 `ansible/inventory/group_vars/` 디렉토리에 있습니다. 환경에 맞게 이 파일들을 수정하시면 됩니다.

## 문서
자세한 문서는 `docs/` 디렉토리에서 찾을 수 있습니다:
- 아키텍처 개요
- 문제 해결 가이드
 