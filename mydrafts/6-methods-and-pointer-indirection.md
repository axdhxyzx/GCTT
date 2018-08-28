### 方法与间接指针(*pointer indirection*)

对比前面两段程序，你可能会注意到带有指针类型参数的函数必须接收一个指针参数：
```go
var v Vertex
ScaleFunc(v, 5) // 编译报错!
ScaleFunc(&v, 5) // 对
```

然而，带有指针类型接收器的方法，在它们被调用时，既可以接收一个值，也可以接收一个指针作为方法的接收器(*receiver*)
```go
var v Vertex
v.Scale(5) // 对
p := &v
p.Scale(10) // 对
```

对于语句```v.Scale(5)```，尽管```v```是一个值，而不是一个指针，但是带有指针类型接收器的方法仍然被自动调用，那是因为Go提供了一种方便，既然```Scale```方法有一个指针类型接收器，那么Go会将语句```v.Scale(5)```转译为```(&v).Scale(5)```。

---

[上一节：指针与函数](https://github.com/axdhxyzx/GCTT/blob/my_branch/mydrafts/5-pointers-and-functions.md) | [返回目录](https://github.com/axdhxyzx/GCTT/blob/my_branch/mydrafts/0-mydrafts-readme.md) | [下一节：方法与间接指针 2](https://github.com/axdhxyzx/GCTT/blob/my_branch/mydrafts/7-methods-and-pointer-indirection-2.md)