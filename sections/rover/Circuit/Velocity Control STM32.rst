Velocity Control STM32
==================

기본 통신 설정
-------------

- **Baudrate**: 921600
- **CRC**: CRC32 (Input/Output Reflected)
- **UART**: UART2 사용

UART 통신 프로토콜
-----------------

UART를 통해 다음과 같은 명령어 모드를 지원합니다:

- **INIT_STATE**: 시스템 초기화
- **SET_SPEED**: 모터 속도 설정
- **CURRENT_SPEED**: 현재 속도 전송
- **SET_BRAKE**: 브레이크 설정
- **SET_PID**: PID 파라미터 설정
- **CURRENT_PID**: 현재 PID 파라미터 전송

CRC 검증 방법
-------------

- UART 데이터의 무결성 검증을 위한 CRC32 (input/output reflected) 사용
- CRC 오류 발생 시 오류 메시지를 반환하여 재시도 유도

코드 구성 요소
-------------

주요 파일:

- **UART_handler.cpp**
  - UART 데이터 수신 및 패킷 파싱
  - 명령어 모드 처리 및 데이터 전송

- **Drive_system.cpp**
  - PID 기반 모터 속도 및 브레이크 제어
  - 속도 측정 및 제어 로직 포함

- **real_main.cpp**
  - 메인 진입점, 시스템 초기화 및 주 루프
  - HAL 설정 (TIM, UART 등) 및 인터럽트 처리

사용 방법
---------

1. **STM32CubeIDE에서 빌드 및 업로드**
2. **UART 통신 설정**
   - RX/TX 기본 버퍼 크기: 24 바이트
3. **명령 사용 예시**:

   - 시스템 초기화: ``INIT_STATE``
   - 속도 설정: ``SET_SPEED``
   - 브레이크 설정: ``SET_BRAKE``
   - PID 설정: ``SET_PID``

주의 사항
---------

- CRC 오류 발생 시 오류 코드 반환
- ID가 0이면 모든 모터에 적용
- DMA 초기화 미진 시 수신 오류 가능성

문의 및 수정
------------

추가 문의 사항은 프로젝트 담당자 또는 팀 이슈 트래커를 활용 바랍니다.


알고리즘
========

RPM 측정 알고리즘
-----------------

``DriveSystem`` 클래스의 ``measureRpm()`` 함수가 RPM 측정을 담당합니다.

1. **DMA 입력 캡처 버퍼 사용**

   - DMA가 버퍼(``m_icDataCh``)에 캡처 값을 순환 저장
   - DMA의 ``NDTR`` 값으로 최근 측정 인덱스 식별

2. **주기(Δt) 계산**

   - 최근 인덱스와 이전 인덱스의 타이머 값 차이 계산
   - Δt (초) = (현재 캡처 값 - 과거 캡처 값) / 타이머 주파수(``TIMER_FREQ``)

3. **주파수를 RPM으로 변환**

   .. math::

      RPM = \frac{60 \times f}{PULSE\_PER\_REV}

   - 예) 엔코더 1024 펄스/회전 시, ``PULSE_PER_REV = 1024``

4. **정지 상태 판정**

   - DMA에 데이터 변화가 없거나 펄스 간격이 비정상이면 정지 상태로 판단

RPM 측정 코드
~~~~~~~~~~~~

.. code-block:: cpp

   double DriveSystem::measureRpm()
   {
       uint32_t ndtr = __HAL_DMA_GET_COUNTER(&m_hdmaIC);
       int currentIndex = wrapIndex(IC_BUF_SIZE - ndtr - 1, IC_BUF_SIZE);
       int prevIndex = wrapIndex(currentIndex - 2, IC_BUF_SIZE);

       uint32_t currentTime = m_icDataCh[currentIndex];
       uint32_t prevTime    = m_icDataCh[prevIndex];

       if (prevTime == 0)
           return 0.0f;

       double dt = static_cast<double>(currentTime - prevTime) / static_cast<double>(TIMER_FREQ);
       if (dt <= 0.0f || isZeroSpeedDetected(currentIndex, 0.4f))
           return 0.0f;

       double frequency = 1.0f / dt;
       double rpm = (60.0f * frequency) / PULSE_PER_REV;
       return rpm;
   }

정지 상태 검출 코드
~~~~~~~~~~~~~~~~~~

.. code-block:: cpp

   bool DriveSystem::isZeroSpeedDetected(int currentIndex, double threshold)
   {
       if (m_icDataCh[m_prev_index] == m_icDataCh[currentIndex])
           m_zero_sampling_stack += 1;
       else
           m_zero_sampling_stack = 0;

       if (m_zero_sampling_stack > 50)
           return true;

       m_prev_index = currentIndex;

       // 추가 펄스 간격 비정상 여부 체크 로직
       return false;
   }

STM32 타이머 설정
-----------------

TIM2 설정
~~~~~~~~~

.. code-block:: c

   void MX_TIM2_Init(void)
   {
       htim2.Instance = TIM2;
       htim2.Init.Prescaler = 1700 - 1;  // 예: 170 MHz → 100 kHz (10 µs)
       htim2.Init.CounterMode = TIM_COUNTERMODE_UP;
       htim2.Init.Period = 4294967295;
       htim2.Init.ClockDivision = TIM_CLOCKDIVISION_DIV1;
       // Input Capture 설정, 양쪽 엣지 감지
   }

PWM 타이머 설정
~~~~~~~~~~~~~~

- TIM1, TIM4 등 PWM 모드 설정
- PWM 듀티 사이클 변경으로 모터 속도 및 방향 제어

결론
-----

- 입력 캡처 + DMA로 정확한 RPM 측정
- PID 제어를 통한 정밀한 모터 제어
- 타이머 설정을 통해 효율적이고 정확한 속도 제어 구현
