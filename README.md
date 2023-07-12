# Welcome to the JDK!

For build instructions please see the
[online documentation](https://openjdk.java.net/groups/build/doc/building.html),
or either of these files:

- [doc/building.html](doc/building.html) (html version)
- [doc/building.md](doc/building.md) (markdown version)

See <https://openjdk.java.net/> for more information about
the OpenJDK Community and the JDK.

# MacBook Pro M2编译JDK17步骤
> 如果有编译失败的话，需要执行命令清除编译文件：make clean；make dist-clean，然后再重新执行第6点

1. 安装xcode
2. 安装其他依赖环境
3. 修改make/autoconf/flags-other.m4文件，具体参考：https://bugs.openjdk.org/browse/JDK-8272700；https://github.com/openjdk/jdk17u/commit/648f3f6a8fe9ea2e00b60710afa44208cfbc2c49
4. 修改src/hotspot/cpu/aarch64/immediate_aarch64.cpp文件，具体参考：https://bugs.openjdk.org/browse/JDK-8280476；https://github.com/openjdk/jdk17u-dev/commit/fbe05ec561e8d2a061be126c969c37c219b594f3
5. 执行命令`ulimit -c unlimited`（如果有报错提示）
6. 执行命令`bash configure --enable-debug --with-native-debug-symbols=internal --with-jvm-variants=client --disable-warnings-as-errors`
7. 执行命令`make images`进行编译
