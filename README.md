# Pwnable (드림핵을 배운 내용을 정리하였습니다)


## 리눅스 메모리구조   
__시스템해킹__ 의 많은 공격은 __메모리 오염__ 을 이용하여 공격합니다.   
그렇기 때문에 메모리구조를 알아야 합니다.   
리눅스에는 5가지 구역으로 나눈 것을 __세그먼트__ 라고 합니다.   
__코드 세그먼트__ , __데이터 세그먼트__ , __BSS 세그먼트__ , __힙 세그먼트__ , __스택 세그먼트__ 가 있습니다.    
이렇게 5가지의 구역을 나누면 필요한 읽기/쓰기/실행 권한을 적절하게 부여할 수 있습니다.    
권한을 부여하면 cpu는 권한이 없는 행동을 할 수 없습니다.
    
## 코드 세그먼트
실행 가능한 기계코드가 위치하는 곳 입니다.   
읽기 권한과 실행 권한이 있습니다. 

## 데이터 세그먼트
값이 정해진 전역 변수와 정적 변수 , 상수 등등.. 이 위치합니다.
rodata와 data세그먼트가 존재하는데
두 차이점은 rodata는 쓰기 권한이 없고
data세그먼트는 쓰기권한이 있습니다.

## BSS 세그먼트
초기화 되지 않은 전역 변수가 위치합니다.
(선언만 하고 초기화 하지 않은 전역변수)
이 구역의 초기화 되지 않은 전역 변수의 값은 0이 됩니다.    
읽기 권한과 쓰기 권한이 부여됩니다.   

## 스택 세그먼트
인자,지역변수 등등... 이 위치합니다.
프로세스의 스택이 위치합니다.
읽기와 쓰기 권한이 부여됩니다.

## 힘 세그먼트
힙 데이터가 위치합니다.
c언어의 malloc()와 같이 호출해서 메모리를 할당 받는 데이터들이 위치합니다.
읽기와 쓰기권한이 부여됩니다.
