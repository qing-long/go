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

