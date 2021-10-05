# restful-api

## 關於本專案
目的: JSON-server建一支RESTful API

## 寫JSON
1. JSON就是JavaScript的陣列
2. 基本上文字都要使用雙引號

## json-server
載入json-server
```
npm install -g json-server
```
啟用json-server並指向JSON檔案
```
json-server --watch db.json
```
## 使用Postman
可以測試 GET/POST/PUT/DELETE

## 建一個RESTful API 
* 測試的URL: http://localhost:3000/users
* REST : GET/POST/PUT/DELETE

### REST 觀念
1. RESTful的核心就是客戶端發出的數據操作指令都是**動詞**+**賓語**
eg: `GET/posts`
2. 動詞都必須是大寫
3. 使用HTTP的方法，對應CRUD(GET/POST/PUT/PATCH/DELETE)
4. 後接的賓語必須是名詞，是HTTP動詞作用的對象。
eg: `/users` 是正確的，但是`/getusers`就是錯誤的

### AXIOS
因為接下來的練習要用axios，所以也提一下!
Axios是一個基於promise的HTTP庫，可以用在瀏覽器或node.js中。
基本上有五種請求方式:
1. get
2. post
3. put 整筆更新
4. patch 局部更新
5. delete

-----

### 實作

#### GET

1. 拿取全部資料
```
axios.get("http://localhost:3000/posts")
 .then(response => {
  console.log(response.data)
  posts.value.push(...response.data)
 })
 .catch(error => console.log(error))
``` 
2. 拿取特定資料
要拿特定的資料就需要帶入參數params
帶入的方法有兩種，一個是直接放在網址內，一個是寫params物件帶入
```
//第一行也可以這樣寫
//axios.get("http://localhost:3000/posts",{params: { ID: 1 }})
axios.get("http://localhost:3000/posts/1")
 .then(response => {
  console.log(response.data)
  posts.value.push(...response.data)
 })
 .catch(error => console.log(error))
```

#### POST

```
axios({
method: "post",
url: "http://localhost:3000/posts",
headers: {
    'Content-type': 'application/json; charset=UTF-8',
},
data: {
    title: post.value.title,
    body: post.value.body
    }
})
.then(response => {
    console.log(response)
})
.catch(error => {
    console.log(error)
})
```

#### DELETE

```
axios({
    method: "delete",
    url: `http://localhost:3000/posts/${id}`,
})
.then(response => {
        console.log(response)
})
.catch(error => {
    console.log(error)
})
```