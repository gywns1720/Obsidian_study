# Material

---
![[Pasted image 20231209115500.png]]

- 위 사진은 머트리얼의 창이다.
- 이름을 지을 때 맨 첫글자 M 을 사용하여 이 파일이 머트리얼이라는 걸 다른 사람에게 알려야 한다.
- MI 라고 적혀있는 Material 은 Material Instance 라고 부른다. (복제본)
- M 파일에 오른쪽 마우스 Create Material Instance 를 눌러 원본 구조를 가진 복제본을 생성합니다.
- 원본이 바뀌면 인스턴스로 원본 머트리얼 구조로 바뀝니다. (파라미터의 인스턴스의 값은 유지 된다.)

## Detail

![[Pasted image 20231209115630.png]]

- 머트리얼의 기본 속성과 종류를 바꿀 수 있습니다.


---

## Graph

![[Pasted image 20231209115705.png]]

- 이곳에서 머트리얼의 대한 속성을 설정 할 수 있습니다.

### Base Color

- 기본적인 색상을 설정 할 수 있습니다.


### Albedo

- Base Color 와 같다.
- Saturation 채도
- Brightness 밝기
- Contrast 색 대비

### Metallic

- 금속(메탈) 재질 
- 반사가 심함
- 특정한 금속 재질 일 때 사용

![[Pasted image 20231209120605.png]]

- 0 ~ 1 사이로 적용할 수 있습니다.
![[Pasted image 20231209120637.png]]

- 금속 재질을 1 로 설정한 경우 위의 이미지 처럼 나타난다.
### Specular

- 얼마만큼 반사를 할건지 적용하는 값
![[Pasted image 20231209121124.png]]
![[Pasted image 20231209121221.png]]
- 비가 올때 젖은 느낌을 들 수 있도록 설정
- Metallic 이 높으면 차이점을 느낄 수 없음.


### Roughness

- 재질의 거칠기 를 나타냅니다.
- 0 이면 매끄러움 , 1이면 거칠어 진다. 
- 즉 0 이면 모든것을 반사 시킵니다.

![[Pasted image 20231209120849.png]]
![[Pasted image 20231209120857.png]]

- metallic 과 같이 사용하면 반사 느낌을 더 강하게 줄 수 있다.

### Anisotropy
- 특수한 재질만 사용함.

### Emissive Color

- 빛나는 물질을 만들 때 사용합니다.

![[Pasted image 20231209121608.png]]

![[Pasted image 20231209121621.png]]

![[Pasted image 20231209121826.png]]
![[Pasted image 20231209121837.png]]



### Opacity

### Opacity Mask

### Normal

- 특정한 이미지 (파란색 같은 재질) 
- 재질의 깊이감을 줄 때 사용 

### Tangent

### World Position Offset

- 특정한 이미지의 위치 (움직일 수 잇음 )
### Subsurface Color

### Custom Data 0

### Custom Data 1

### Ambient Occlusion

- 텍스쳐를 만들 때 굴곡 부분에 그림자가 생기는데 그런 사이 그림자를 조절하는 옵션
- 빛이 아닌 텍스쳐로 생긴 그림자
### Refraction

### Pixel depth offset

### Shading Model