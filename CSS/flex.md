### Flex

### Flex basis & Flex grow 함께 사용하기

- 자식에게 적용하는 속성

flex-grow, flex-shrink 만 쓸경우 *여백*을 설정한 비율만큼 나눠가진다
실제로 1 : 2 : 1 의 비율만큼 공간을 차지하고 싶다면
flex-basis : 0 으로 설정해준다

> 원리 : 모든 자식에게 flex-basis : 0 을 줘서 모든 부분을 여백으로 인식하게 끔 한 뒤
> flex-grow(늘어날 때),flex-shrink(줄어들 때) 로 여백을 분배해 주면 원하는 공간만큼 차지하게 된다

#

### `flex-bsis: 0 && flex-grow: 1 && flex-shrink: 1` 의 축약형

> `flex: 1 ` ( `flex-basis: 0 `이 자동으로 세팅 된다)

#

> flex item 중 어떤 item은 고정시키고
> 다른 item은 화면이 늘어남에 따라 늘어나게 하고 싶을 땐
> 고정시키는 것은 flex라는 속성을 주지 않고
> 늘어나게 하고 싶은 item 만 flex:1 이런식으로 속성을 준다

### 남은 공간만큼 꽉 채우고 싶을 때(위 내용 활용)

```css
.videos-row-container {
  position: relative;
  /* background-color: pink; */
  /* height: 28vh; */
  height: 65vh;
  width: 100vw;
  padding: 20px;
  display: flex;
  flex-direction: column;
}

.videos-row-container .row-title {
  font-size: 2.2rem;
  letter-spacing: 0.8px;
  font-weight: 600;
  padding: 5px 0;
  color: var(--main-white-color);
}

.videos-row {
  display: flex;
  /* flex 설명 */
  flex: 1;
  /* 여기 수정!!! */
  min-width: 300vw;
  transition: transform 200ms ease-in-out;
  overflow-x: scroll;
}
```

> 1.  부모컨테이너를 `display:flex`로 설정한다
> 2.  부모의 자식은 *row-title*과 *videos-row*가 있다
> 3.  title상자의 크기는 반응형에 따라 font-size가 달라지고, 그에 따라 title 상자가 차지하는 공간도 달라진다
> 4.  부모컨테이너의 높이도 화면 크기에 따라 달라지기 때문에 videos-row 가 화면의 크기의 달라짐에 상관없이 남은 공간을 채우기 위해서는 _flex: 1_ 을 설정해준다
