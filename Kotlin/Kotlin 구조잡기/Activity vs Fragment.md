# Activity vs Fragment 어떤걸 사용하는게 더 좋을까?

 프래그먼트는 기본적으로 태블릿과 같은 큰화면에서 역동적이고 유연한 UI디자인을 지원하는것이 목적이었다. 태블릿의 화면은 휴대폰 화면보다 훨씬 크기 때문에 UI 구성요소 조합과 표현할 공간이 더 많다.
<div align=center>
  
![image](https://github.com/lch9772/TIL/assets/73581653/480fb570-c519-4f13-a386-56f75151d7c9)

</div>

 프래그먼트를 사용하면 앞의 그림과 같이 Master-Detail 구조를 갖는 구현을 손쉽게 구현할 수 있다.
이 외에도 NavigationDrawer, BottomSheetDialog, Navigation Component 등을 구현할 때 프래그먼트가 사용된다.
