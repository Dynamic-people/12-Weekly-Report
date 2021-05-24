# 12-Weekly-Report
※코드는 Code Repository를 참고해주세요


다음은 버튼을 눌렀을 때 호출되는 리스너이다. '버튼 누르면 수행 할 명령'에 파이어베이스로 데이터를 보내는 코드는

      button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                databaseReference.child("menu").push().setValue("아이스 카페 아메리카노");
                Intent intent = new Intent(getApplicationContext(), ordersheet.class);
                startActivity(intent);
            }
        });
        
데이터 입력 방식에는 크게 두 가지가 있다.

         databaseReference.child("").push().setValue("2");
         databaseReference.child("menu").child("aaa").setValue("2");


child("menu")는 JSON 데이터 형식에서 데이터의 '이름' 값을 의미한다.
child("menu").child("aaa").setValue("2")를 해석해보자면 menu - aaa 항목의 값을 "2"로 덮어씌운다는 뜻이다. 
기존 menu - aaa 항목이 존재하지 않다면 새로 생성된다.

push()는 특정한 규칙의 child를 임의로 생성하면서 값을 넣는다.

child("menu").push().setValue("아이스 카페 아메리카노");를 해석해보자면 menu 이름값 하위에 특정한 규칙을 가진 
child를 생성하면서 그 값을 "아이스 카페 아메리카노"로 셋팅한다는 것이다.

push()를 사용할 경우 새로만들기 개념이므로 채팅 데이터가 쌓이듯이 데이터가 쌓이게 된다.

따라서,,

#### * 주문서 화면에서 원하는 메뉴 클릭시

메뉴 클릭시 포스기에서 확인할 수 있게 'firebase 실시간 데이터베이스'에 데이터가 저장된다.

![ezgif com-gif-maker](https://user-images.githubusercontent.com/79883718/119328980-ac465d00-bcbf-11eb-9bc7-757b4a7fe970.gif)


#### 주문서 카카오계정과 연동
 주문을 했을때 카카오API로 받은 이름을 넣어서 주문서를 분간해줌
![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/79992109/119342712-6e9e0000-bcd0-11eb-92a7-983414927a99.gif)




#### 앱의 진동벨 기능

카페에서 따로 진동벨을 받지않아도 제조완료된 음료알림을 앱으로 받을 수 있는 푸시알림을 구현하였다.
코드에는 오류가 없지만 포스기역할(firebase)의 데이터에서 알림을 보내는 과정에서 문제가 생겨서 다음주까지 해결할 예정이다.

![image](https://user-images.githubusercontent.com/75411735/119341905-4cf04900-bccf-11eb-8ad8-24b5c664e437.png)


#### POS

데이터들을 보여주기 위한 ListView를 사용하기 위해 정의된 데이터를 받아 List에 사용 될 View를 생성하고 관리하는 역할인 Adapter를 이용해 
데이터들을 나타내고 ArrayList로 데이터들을 순서대로 나타내주었다.

![2 code1](https://user-images.githubusercontent.com/80111309/119360001-20dfc280-bce5-11eb-830d-b3d48e7da4db.PNG)
![2 code2](https://user-images.githubusercontent.com/80111309/119360348-79af5b00-bce5-11eb-93c2-f962efe9bd14.PNG)

위의 사진은 예제로 만들어 본 것이고 다음 주에 주문서에 작성된 주문들을 데이터베이스 연결을 통해 순서대로 나타나게 할 예정이다.


첫 메인 화면에서 주문서 아이콘을 누르면 주문내역을 볼 수 있다.

![1](https://user-images.githubusercontent.com/80111309/119360573-b713e880-bce5-11eb-849e-6e93a4ca897a.PNG)
![2](https://user-images.githubusercontent.com/80111309/119360594-bbd89c80-bce5-11eb-8e6d-fb6f41287ca7.PNG)

그 다음 종료 아이콘을 누르면 AlertDialog로 만든 알림창이 뜨면서 종료를 할 것인 지 물어보고 NO를 누르면 원래 화면으로 돌아가고 
YES를 누르면 종료하게 된다.

![3](https://user-images.githubusercontent.com/80111309/119360806-f7736680-bce5-11eb-86e9-d4fa6f25de3c.PNG)
![3 code](https://user-images.githubusercontent.com/80111309/119360831-fe01de00-bce5-11eb-9bfe-c122bd911b24.PNG)



