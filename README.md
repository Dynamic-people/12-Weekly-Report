# 12-Weekly-Report

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
기존 message - aaa 항목이 존재하지 않다면 새로 생성된다.

push()는 특정한 규칙의 child를 임의로 생성하면서 값을 넣는다.

child("menu").push().setValue("아이스 카페 아메리카노");를 해석해보자면 menu 이름값 하위에 특정한 규칙을 가진 
child를 생성하면서 그 값을 "아이스 카페 아메리카노"로 셋팅한다는 것이다.

push()를 사용할 경우 새로만들기 개념이므로 채팅 데이터가 쌓이듯이 데이터가 쌓이게 된다.

따라서,,

#### * 주문서 화면에서 원하는 메뉴 클릭시

메뉴 클릭시 포스기에서 확인할 수 있게 'firebase 실시간 데이터베이스'에 데이터가 저장된다.

![ezgif com-gif-maker](https://user-images.githubusercontent.com/79883718/119328980-ac465d00-bcbf-11eb-9bc7-757b4a7fe970.gif)
