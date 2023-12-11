---
tags:
  - 언리얼
  - "#Texture"
---
# Texture

---

![[Pasted image 20231209111340.png]]

## 디테일 정보 

### Level Of Detail

#### LOD Blas

- 해당 값 설정으로 Texture 파일의 해상도를 줄일 수는 있지만 용량 자체를 줄여주진 않는다.
![[Pasted image 20231209111620.png]]

- LOD Bias 를 1로 주었을 때 `1/2 * 1/2` 계산이 적용되어 2048x2048 해상도를 보여줍니다.
- Imported 가 이 파일의 원본 텍스쳐 해상도 이며, Displayed 가 게임에 사용될 텍스쳐 해상도 입니다.
- 2인 경우 `1/4 * 1/4` 인 `1/16` 의 해상도로 볼 수 있다.

---

## Normal Texture

![[Pasted image 20231209112305.png]]

- 이런 파란색 이미지는 노멀 텍스쳐라 부른다.
- 사물의 굴곡을 표현하는 텍스쳐


---

## 텍스쳐를 활용한 머트리얼 작업

- 이미지 파일을 노드 안에 드래그 후 Base Color 적용

![[Pasted image 20231209122829.png]]

![[Pasted image 20231209122919.png]]

![[Pasted image 20231209123136.png]]

![[Pasted image 20231209123142.png]]

![[Pasted image 20231209123756.png]]

- 언리얼 엔진은 흰색은 1, 검은색 부분은 0 으로 인식한다.