# [ Vue ]

## < 세팅 >

1. npm install -g @vue/cli@4.5.11
2. 프로젝트 폴더 생성 후 오픈
3. vue create 프로젝트명

## < 미리보기 >

- npm run serve

## < 데이터바인딩 >

- HTML 속성에 데이터 쓸 때
  - <h4 :style="color">XX 원룸</h4>

## < 반복문: v-for >

- <a v-for="작명 in 메뉴들" :key="작명">Home</a>
- <a v-for=“(작명, idx) in 메뉴들" :key=“idx”>Home</a>

## <이미지 넣을 때>

- <img src="./경로">
    - public 폴더에 넣으면 나중에 발행할 때 이미지가 이름이 변하지않습니다
    -  src는 임의로 바꿔줌

## <커스텀이벤트 전달> : 자식 → 부모에게 데이터변경을 요청할 때

- 자식: @click=“$emit(‘openModal’, a.id)”
- 부모: @openModal=“open = true; target = $event;”

## <v-model>

- v-model에 입력된 값을 data로 바로 저장해주세요~
- <input @input="month = $event.target.value" /> 는
- <input v-model=“month” /> 로 쓸 수 있다

## <watch : 데이터 감시>

- 함수명을 감시하고자하는 데이터명으로
- 해당 데이터가 변할 때 마다 코드가 실행됨
- 파라미터: 첫 번째 - 변경될 값, 두 번째 - 변경전 값

## <조건부 클래스명>

- 쓰던 방법: 해당 컴포넌트를 fragment로 감싸주고 클래스 부여
- <div class=“효과전클래스” :class=“{부착클래스: true}”>

<Transition>
- fragment에 메인 name을 부여 → 
```
<transition name=“fade”></transition>
```
- 들어갈 때: fade-enter-from/active/to
- 끝날 때 : fade-leave-from/active/to
