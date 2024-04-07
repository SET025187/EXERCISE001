$$
`memset` 是一个 C/C++ 标准库函数，用于将一块内存区域的值设置为指定的数值。

函数原型如下：

```cpp
void *memset(void *ptr, int value, size_t num);
```

参数说明：
- `ptr`：指向要设置值的内存区域的指针。
- `value`：要设置的值，通常是一个无符号字符或整数。
- `num`：要设置的字节数。

函数功能：
`memset` 将 `ptr` 指向的内存区域的前 `num` 个字节都设置为 `value`。

使用 `memset` 可以快速地将一块内存区域初始化为指定的数值，例如将数组初始化为全 0 或全 -1。

以下是一个示例：

```cpp
#include <cstring>
#include <iostream>

int main() {
    int arr[5];
    std::memset(arr, 0, sizeof(arr));

    for (int i = 0; i < 5; ++i) {
        std::cout << arr[i] << " ";
    }
    // 输出：0 0 0 0 0

    return 0;
}
```

在上述示例中，`memset(arr, 0, sizeof(arr))` 将数组 `arr` 的每个元素都设置为 0。`sizeof(arr)` 返回数组 `arr` 的总字节数，用于确定要设置的字节数。
$$

