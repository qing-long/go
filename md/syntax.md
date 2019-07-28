## Go syntax

## `...`


- 指定容器固定长度

```go
s := [...]string{"1", "2", "3"}
```

- 接受不定长的参数

```go
func s(s ...int) {
	for i := 0; i < len(s); i++ {
		fmt.Println(s)
	}
```

- 传入不定长的参数

```go
func S(s ...string) {
	for i := 0; i < len(s); i++ {
		fmt.Println(s)
	}
}
```

