## gin


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