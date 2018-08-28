### 方法与间接指针 2

反过来，在值类型上会发生同样的事情。

带有一个值类型参数的函数，必须接收那个具体类型的值：
```go
var v Vertex
fmt.Println(AbsFunc(v)) // 对
fmt.Println(AbsFunc(&v)) // 编译报错！
```

然而带有值类型接收器的方法，当它们被调用时，既可以接收一个值，也可以接收一个指针作为方法的接收器：
```go
var v Vertex
fmt.Println(v.Abs()) // 对
p := &v
fmt.Println(p.Abs()) // 对
```

在这种情况下，方法调用语句```p.Abs()```被翻译为```(*p).Abs()```。