## 이미지를 req.file로 받아오는데 undefined가 뜸
백의 문제가 아닌 프론트의 문제였다. 
1. 프론트에서 FormData가 아닌 URLSearchParams를 썼다. (FormData 써야함)
2. 프론트에서도 multer를 설치해야 한다