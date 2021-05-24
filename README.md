# 12-Weekly-Report
※코드는 Code Repository를 참고해주세요

### [DATERBASE]
##### -김윤경, 변예인, 최재원
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


#### * 주문서 카카오계정과 연동
 주문을 했을때 카카오API로 받은 이름을 넣어서 주문서를 분간해줌
![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/79992109/119342712-6e9e0000-bcd0-11eb-92a7-983414927a99.gif)




#### * 앱의 진동벨 기능

카페에서 따로 진동벨을 받지않아도 제조완료된 음료알림을 앱으로 받을 수 있는 푸시알림을 구현하였다.
코드에는 오류가 없지만 포스기역할(firebase)의 데이터에서 알림을 보내는 과정에서 문제가 생겨서 다음주까지 해결할 예정이다.

![image](https://user-images.githubusercontent.com/75411735/119341905-4cf04900-bccf-11eb-8ad8-24b5c664e437.png)



### [주문서 구현]
##### -전수아
기존에 웹뷰를 이용하여 html페이지를 연결시키려하여 html 웹페이지를 제작하였지만, 안드로이드 스튜디오 내에 직접 주문서를 올리게 하는 방식으로 변경되어, 안드로이드스튜디오로 주문서를 제작하였다

<img width="305" alt="주문서1" src="https://user-images.githubusercontent.com/79993772/119361142-4b7e4b00-bce6-11eb-9bfe-6791c93cf024.png">
<img width="302" alt="주문서2" src="https://user-images.githubusercontent.com/79993772/119361167-53d68600-bce6-11eb-954e-d8840a74907c.png">



## POS
##### -최민진
데이터들을 보여주기 위한 ListView를 사용하기 위해 정의된 데이터를 받아 List에 사용 될 View를 생성하고 관리하는 
역할을 하는 Adapter를 이용하고 ArrayList로 데이터들을 순서대로 나열할 수 있게 구현하였다.

![2 code1](https://user-images.githubusercontent.com/80111309/119367657-250fde00-bced-11eb-9046-7707a938dcae.PNG)
![2 code2](https://user-images.githubusercontent.com/80111309/119367679-29d49200-bced-11eb-8ac9-a8c439628a26.PNG)

이렇게 해서 다음 주에는 주문서로 작성된 주문들을 데이터베이스 연결을 통해 불러와서 보여지게 할 예정이다.

#### 첫 메인 화면과 주문서 아이콘을 누르면 나오는 주문내역 화면
![1](https://user-images.githubusercontent.com/80111309/119367891-61433e80-bced-11eb-87c2-ec5e77d75abb.PNG)
![2](https://user-images.githubusercontent.com/80111309/119367905-656f5c00-bced-11eb-832b-090600f92e2d.PNG)

앞으로 주문내역에서 승인/거절을 할 수 있는 버튼도 구현할 예정이다.

#### 종료 기능
![3](https://user-images.githubusercontent.com/80111309/119368016-86d04800-bced-11eb-97a2-86e9d86323b5.PNG)
![3 code](https://user-images.githubusercontent.com/80111309/119368054-8f288300-bced-11eb-9e03-bae1a9988c34.PNG)

AlertDialog를 이용해 종료 아이콘을 누르면 정말 종료하겠냐고 물어보는 알림창이 떠서
NO를 누르면 원래 화면으로 돌아가고 YES를 누르면 종료되는 기능을 구현하였다.
