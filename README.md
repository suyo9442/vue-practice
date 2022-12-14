

# 어떤 상황?
- 컴포넌트가 마운트 되자마자 1씩 감소하고, 0에서 멈추는 기능을 구현하고 있었다.
- 기존코드

```
mounted() {
    // 1️⃣ 1씩 감소하는 함수 생성
    const play = () => {
        this.sale--;
    }

    if (this.sale !== 0)
    setInterval()
}
```



## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
