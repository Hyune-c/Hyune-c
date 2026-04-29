# 배포 후 인스턴스가 기동되지 않는 오류

## 배경

- 배포 후 인스턴스가 간헐적으로 정상 기동되지 않는 현상이 발생했습니다.
- 확인 결과 health check 간격이 1분으로 너무 짧아, 최초 기동 중 간헐적인 실패가 발생했습니다.

## 개선

배포 직후 기동 단계에서 health check 실패가 발생하는 것을 확인했습니다.

![기동 실패 로그](./assets/kurly-startup-probe-image-01.png)

원인은 최초 기동 중 아직 준비되지 않은 인스턴스를 livenessProbe 가 너무 빠르게 실패로 판단하는 것이었습니다.

- 기동 초기에만 더 긴 유예 시간을 주도록 startupProbe 를 조정했습니다.
- 이후 상태를 체크하는 livenessProbe 는 유지하여, 기동 시점과 운영 중 상태 체크의 책임을 분리했습니다.

![Probe 설정](./assets/kurly-startup-probe-image-03.png)

설정 변경 후 배포 흐름에서 인스턴스가 안정적으로 기동되는지 확인했습니다.

![배포 흐름 확인](./assets/kurly-startup-probe-image-02.png)
