# ⚙️ 디자인패턴 

##  📌 01. 인스턴스 생성과 관리

### 1. Singleton

<img src="https://github.com/jongheonleee/design_pattern_java/assets/87258372/d2563b0e-b38e-464b-9427-6d6f0b29496a" width="500" height="500"/>


> ### 👉 인스턴스 하나만 생성하고 공유한다
  
- 자원을 절약하려는 의도, 무분별하게 new 연산자 하는 것을 막음 
- 인스턴스가 하나만 생성되는 것을 보증 해야한다 
- 공유하기 때문에 멀티쓰레드 환경에서 인스턴스 변수(iv) 값이 임의로 변경되는 것을 막아야한다
- iv가 없는게 좋음, 있어야하면 동기화 처리가 된 것을 사용하거나 상수를 사용해야함, 또한 iv에 계산된 값을 저장하기 보다는 메서드로 반환하는 게 좋음

> ### 👉 스프링에서 컨테이너에 빈 등록할 때, 기본적으로 Singleton으로 등록

- 빈으로 등록할 객체는 정보 공유가 가능한지, 멀티 쓰레드 환경에서 iv 오염이 발생하지 않는지 고려

### 2. Flyweight

<img src="https://github.com/jongheonleee/design_pattern_java/assets/87258372/3dd289aa-297c-48d0-a635-67251501da59" width="500" height="500"/>

> ### 👉 n개의 인스턴스를 한번만 생성하고 맵에 등록하여 공유한다  

- Singleton 의 확장 버전, Singleton은 인스턴스 1개 생성을 절약하려는 의도. Flyweight는 인스턴스 n개 생성을 절약하려는 의도
- FlyweightFactory에 Singleton 적용, Map으로 생성한 인스턴스를 등록하고 관리
- 공유하기 때문에 멀티 쓰레드 환경에 주의해야함. 즉 Flyweight를 적용할 인스턴스가 무거운지, 공유 가능한 인스턴스인지 따져 봐야함
- getFlyweight()메서드가 동기화 처리되야함. 예를 들어, 서로 다른 쓰레드가 동시에 같은 인스턴스를 사용하길 원하고 해당 인스턴스가 없는 경우 여러번 생성될 수 있음 

> ### 👉 스프링에서 컨테이너 구조와 매우 유사

- 스프링은 제어의 역전, 즉 사용과 생성을 분리함. 따라서, 스프링 컨테이너에서 빈을 생성 및 등록 그리고 관리해줌(생성). 개발자는 해당 빈을 사용하기만 하면됨
- 물론, 빈은 크게 두 부류로 등록됨, Singleton과 Prototype으로 등록됨
- Flyweight는 Singleton 사용함 
