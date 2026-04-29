# 컬리몰 상품권 구매 프로세스 개선

런칭 후 장애가 발생하면 양사 간 데이터 불일치가 생기고 수동 대응이 필요한 구조였습니다.  
기존 Go 로직과 Kotlin/Spring 신규 흐름을 연계하면서, 불일치는 Kafka 기반 결과적 일관성으로 복구 가능한 방향을 설계했습니다.

![캡처 1](./assets/kurlymall-giftcard-process-image-01.png)
![캡처 2](./assets/kurlymall-giftcard-process-image-02.png)
![캡처 3](./assets/kurlymall-giftcard-process-image-03.png)
![캡처 4](./assets/kurlymall-giftcard-process-image-04.png)
![캡처 5](./assets/kurlymall-giftcard-process-image-05.png)
