 ## 캔버스는 태그에서 지정하는 width, height랑 css의 width, height는 다르다
* css에서의 width, height는 사용자에게 보여주는 크기이고, canvas tag에서의 크기 지정은 실제의 캔버스 크기이다. 두개의 개념 혼동주의!!
* 실제로 보여줄려고 하는 크기의 두배정도를 canvas 태그의 크기로 지정하고 css에서 실제크기를 지정한다. why?
* 왜냐하면 canvas는 픽셀 방식이기때문에 사용자에게 고화질로 보여주기 위해서는 크기 그리는게 좋다. 압축해서 보여주는게 픽셀이 안보이고 고화질이 가능하기 때문, 대신 성능 이슈와 계산할 픽셀의 값이 많이지는 단점이 있음.

## canvas 태그 안에 text를 입력하면 canvas를 지원하지 않는 브라우저일 경우 text가 보인다.

* fillRect : 칠하는 개념 /검은색이 default값이다  /fillRect(x좌표,y좌표, 넓이, 높이);
* fillStyle = 'red' 직접 색상 지정가능하나, 모든 fillRect의 색상이 바뀌는 것이 아닌 이후의 색상만 바뀜
* 모든 것은 도화지에 그리는것 처럼 순서대로
* clearRect : 지우개
* strokeRect : 선 그리기(사각형)
* beginPath : 선그리기 시작
* moveTo : 선의 시작점
* lineTo : 선의 방향점
* closePath : 선그리기 종료
* context.arc(300, 200, 50, 0, 라디안(360), false);
 -(중심의 x, 중심의y, 반지름크기, 시작각도, 끝각도, 불린값)
 -라디안(360) 파이값으로 구해야한당.
 -360도는 = 2파이
 -불린값은 호의 방향,  true 반시계, false 시계방향 지정

 ## 애니메이션화 하기

 * requestAnimationFrame()은 함수를 넣어주면 반복을 시켜준다. 1초에 60번 반복 default
 * setInterval()은 반복할 함수와 시간, 1000이 1초 로 반복을 시켜줌
 * requestAnimationFrame()의 사용률이 높은데,  애니메이션 화의 경우
 계속 반복을 시켜주는데 setInterval은 그리는 연산이 복잡한경우 그릴준비가 되기 전에 반복을
 하기때문에 불안정하고, 프레임이 유실될 경우가 있다. 반면 requestAnimationFrame은 그점을 보완해 그릴 준비가 다 되었을때까지 기다렸다가 반복을 시켜준다.
 * requestAnimationFrame()은 시간 조절을 할 수 없는데 이경우 나누기를 이용하여 시간 조절을 할 수 있다. count 변수를 사용하여 ++를 시켜준후 나누기를 해서 가능