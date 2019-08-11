# go

> go notes

### 必须要掌握的技能


- [ ] 基本语法
- [ ] 条件语句
- [ ] 错误处理
- [ ] 设计模式
- [ ] go 标准库
- [x] pre commit hook
- [ ] gin
	- [x] gin project structure
	- [x] gin hello world
	- [x] gin || golang dockerfile
	- [ ] argument parse


- pre commit hook

```yaml
- repo: git://github.com/dnephin/pre-commit-golang
  rev: master
  hooks:
    - id: go-fmt
    - id: go-lint
    - id: go-unit-tests
    - id: go-build
- repo: git://github.com/pre-commit/pre-commit-hooks
  rev: v0.7.1
  hooks:
    - id: trailing-whitespace
```
