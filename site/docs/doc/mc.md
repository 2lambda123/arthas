# mc

[`mc-retransform`在线教程](https://arthas.aliyun.com/doc/arthas-tutorials?language=cn&id=command-mc-retransform)

::: tip
Memory Compiler/内存编译器，编译`.java`文件生成`.class`。
:::

```bash
mc /tmp/Test.java
```

可以通过`-c`参数指定 classloader：

```bash
mc -c 327a647b /tmp/Test.java
```

也可以通过`--classLoaderClass`参数指定 ClassLoader：

```bash
$ mc --classLoaderClass org.springframework.boot.loader.LaunchedURLClassLoader /tmp/UserController.java -d /tmp
Memory compiler output:
/tmp/com/example/demo/arthas/user/UserController.class
Affect(row-cnt:1) cost in 346 ms
```

可以通过`-d`命令指定输出目录：

```bash
mc -d /tmp/output /tmp/ClassA.java /tmp/ClassB.java
```

编译生成`.class`文件之后，可以结合[retransform](retransform.md)命令实现热更新代码。

::: warning
注意，mc 命令有可能失败。如果编译失败可以在本地编译好`.class`文件，再上传到服务器。具体参考[retransform](retransform.md)命令说明。
:::
