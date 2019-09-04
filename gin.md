## gin


- gin project structure(暂定)

```golang
.
├── Dockerfile       // docker file
├── README.md        // README
├── config           // 配置层
├── controller       // 控制层
│   └── auth
│       └── login.go // login
├── go.mod           // go mod
├── go.sum           // go mod
├── helper           // 包装的返回值一些方法
│   └── response.go
├── main.go          // 程序的入口
├── model            // 模型
├── route            // 配置路由
│   └── router.go
└── util             // 工具函数
```


- gin hello world


```golang
package main

import (
	"github.com/gin-gonic/gin"
	"net/http"
)

func main() {
	router := gin.Default()

	router.GET("/", func(c *gin.Context) {
		c.String(http.StatusOK, "It works")
	})

	err := router.Run(":8080")
	if err != nil {
		panic("not my fault")
	}
}
```

- gin || golang dockerfile


```bash
FROM golang:1.11 AS builder

WORKDIR /tmp/build/

COPY . .

ENV GOPROXY=https://goproxy.io

RUN rm -rf go.sum && go mod download

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GOARM=6 go build -o app .

FROM alpine:latest

COPY --from=builder /tmp/build/app .

RUN chmod a+x ./app

EXPOSE 8080

CMD ["./app"]
```


- gin argument parse

`getQuery`

```golang
func (Friend) GetNewFriends(ctx *gin.Context) {
	wxid, ok := ctx.GetQuery("wxid")
	if !ok {
		helper.RespFail(-1, "wxid 是必须的参数", http.StatusBadRequest)
		return
	}

	records, err := ninth_studio.GetNewFriendRecords(wxid)
	if err != nil && err != gorm.ErrRecordNotFound {
		log.Error().Err(err).Msgf("GetNewFriends GetNewFriendRecords fail wxid %v ", wxid)
		helper.RespFail(-1, "记录未找到", http.StatusNotFound)
		return
	}

	data := weffect_service.FormatNewFriends(records)
	helper.RespSuccess(data, "OK")
	return
}
```

`ShouldBind`

```golang
func GetUserInfo(ctx *gin.Context) {
	var param weffect_service.UserParam

	err := ctx.ShouldBind(&param)
	if err != nil {
		log.Error().Err(err).Msgf("GetUserInfo ShouldBind fail")
		helper.RespFail(-1, "fail", 400)
		return
	}
```

