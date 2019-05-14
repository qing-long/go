## 选择语句



### if

example:

```go
func If() {
	a := 1
	if a > 1{
		fmt.Println("some")
	} else if a < 0 {
		fmt.Println("some2")
	} else {
		fmt.Println("some3")
	}
}
```