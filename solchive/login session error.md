## 세션이 유지되지 않아 로그인 체크가 안됨

서버는 기본적으로 다른 도메인으로부터 온 요청에 대해서는 쿠 설정 및 응답해주지 않는다.
따로 cors와 withCredentials 설정해줘야 함

서버에서 
1. origin 특정 url로 변경   
2. credentials true로 변경  

```app.use(cors({
    origin: 'http://localhost:3000',
    credentials: true
}));```

3. 헤더 추가    
```app.use((req, res, next) => {
    res.setHeader('Access-Control-Allow-Origin', 'http://localhost:3000');
    res.header('Access-Control-Allow-Methods', 'GET, PUT, POST, DELETE, OPTIONS');
    res.setHeader('Access-Control-Allow-Headers', 'Content-Type, Authorization, Content-Length, X-Requested-With, origin');
    res.setHeader('Access-Control-Allow-Credentials', true);
    (req.method === 'OPTIONS') ?
    res.send(200) :
    next();
})```

클라이언트에서 정보를 보내는 쪽과 받는 쪽 모두 credentials: 'include' 추가  
withCredentials: true는 되지 않았음