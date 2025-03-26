# C++ 标准库头文件列表及作用说明

以下是 C++ 标准库的主要头文件列表及其作用说明（基于 C++20 标准）：

## 1. 标准 C 库头文件（兼容 C）

| 头文件 | 作用 |
|--------|------|
| `<cassert>` | 提供断言宏 `assert` |
| `<cctype>` | 字符处理函数（如 `isalpha`, `toupper`） |
| `<cerrno>` | 错误号宏和 `errno` 变量 |
| `<cfenv>` | 浮点环境访问 |
| `<cfloat>` | 浮点数特性宏（如 `FLT_MAX`） |
| `<cinttypes>` | 格式化整数类型和宏 |
| `<ciso646>` | 运算符宏（C++20 已弃用） |
| `<climits>` | 整数类型特性宏（如 `INT_MAX`） |
| `<clocale>` | 本地化函数和宏 |
| `<cmath>` | 数学函数（如 `sin`, `sqrt`） |
| `<csetjmp>` | 非局部跳转（`setjmp`/`longjmp`） |
| `<csignal>` | 信号处理 |
| `<cstdarg>` | 可变参数处理（如 `va_start`） |
| `<cstdbool>` | 布尔宏（C++20 已弃用） |
| `<cstddef>` | 基本类型和宏（如 `size_t`, `NULL`） |
| `<cstdint>` | 固定宽度整数类型（如 `int32_t`） |
| `<cstdio>` | C 风格输入/输出（如 `printf`, `scanf`） |
| `<cstdlib>` | 通用工具（如 `malloc`, `rand`） |
| `<cstring>` | C 风格字符串处理（如 `strcpy`, `strlen`） |
| `<ctgmath>` | 类型通用数学函数（C++17 已弃用） |
| `<ctime>` | 时间/日期处理（如 `time`, `clock`） |
| `<cuchar>` | Unicode字符处理 |
| `<cwchar>` | 宽字符处理 |
| `<cwctype>` | 宽字符分类和转换 |

## 2. 容器相关头文件

| 头文件 | 作用 |
|--------|------|
| `<array>` | 固定大小数组容器 |
| `<vector>` | 动态数组容器 |
| `<deque>` | 双端队列容器 |
| `<forward_list>` | 单向链表容器 |
| `<list>` | 双向链表容器 |
| `<map>` | 关联数组（键值对）容器 |
| `<set>` | 有序集合容器 |
| `<unordered_map>` | 哈希表实现的关联数组 |
| `<unordered_set>` | 哈希表实现的集合 |
| `<stack>` | 栈适配器 |
| `<queue>` | 队列适配器（包含 `priority_queue`） |
| `<span>` (C++20) | 非拥有序列视图 |

## 3. 算法与迭代器

| 头文件 | 作用 |
|--------|------|
| `<algorithm>` | 通用算法（如 `sort`, `find`） |
| `<execution>` (C++17) | 并行算法执行策略 |
| `<numeric>` | 数值算法（如 `accumulate`） |
| `<iterator>` | 迭代器定义和工具 |

## 4. 字符串处理

| 头文件 | 作用 |
|--------|------|
| `<string>` | `std::string` 和 `std::wstring` |
| `<string_view>` (C++17) | 字符串视图 |
| `<charconv>` (C++17) | 字符转换（如 `to_chars`） |
| `<regex>` | 正则表达式支持 |

## 5. 输入/输出

| 头文件 | 作用 |
|--------|------|
| `<iostream>` | 标准输入/输出流（`cin`, `cout`） |
| `<fstream>` | 文件流 |
| `<sstream>` | 字符串流 |
| `<iomanip>` | 流操纵器（如 `setw`, `setprecision`） |
| `<ios>` | 基本流特性 |
| `<iosfwd>` | 流类的前向声明 |
| `<istream>` | 输入流基类 |
| `<ostream>` | 输出流基类 |
| `<streambuf>` | 流缓冲区类 |

## 6. 多线程与并发

| 头文件 | 作用 |
|--------|------|
| `<thread>` | 线程支持 |
| `<mutex>` | 互斥锁 |
| `<shared_mutex>` (C++14) | 共享互斥锁 |
| `<future>` | 异步结果处理 |
| `<condition_variable>` | 条件变量 |
| `<atomic>` | 原子操作 |
| `<latch>` (C++20) | 线程同步门闩 |
| `<barrier>` (C++20) | 线程屏障 |
| `<semaphore>` (C++20) | 信号量 |

## 7. 内存管理

| 头文件 | 作用 |
|--------|------|
| `<memory>` | 智能指针（`shared_ptr`, `unique_ptr`）和内存工具 |
| `<memory_resource>` (C++17) | 多态内存资源 |
| `<new>` | 动态内存管理（如 `operator new`） |
| `<scoped_allocator>` | 嵌套分配器支持 |

## 8. 日期与时间

| 头文件 | 作用 |
|--------|------|
| `<chrono>` | 时间库（如 `system_clock`） |
| `<date>` (C++20) | 日历日期支持 |

## 9. 类型支持

| 头文件 | 作用 |
|--------|------|
| `<typeinfo>` | 运行时类型信息（`typeid`） |
| `<typeindex>` | 类型索引 |
| `<type_traits>` | 类型特性（如 `is_integral`） |
| `<limits>` | 数值特性（如 `numeric_limits`） |
| `<variant>` (C++17) | 类型安全联合 |
| `<any>` (C++17) | 任意类型容器 |
| `<optional>` (C++17) | 可选值容器 |
| `<compare>` (C++20) | 三路比较支持 |
| `<concepts>` (C++20) | 概念定义 |

## 10. 异常处理

| 头文件 | 作用 |
|--------|------|
| `<exception>` | 异常基类和异常处理工具 |
| `<stdexcept>` | 标准异常类（如 `runtime_error`） |

## 11. 实用工具

| 头文件 | 作用 |
|--------|------|
| `<utility>` | 通用工具（如 `pair`, `move`） |
| `<tuple>` | 元组支持 |
| `<functional>` | 函数对象和绑定器 |
| `<bitset>` | 位集合容器 |
| `<initializer_list>` | 初始化列表支持 |
| `<random>` | 随机数生成 |
| `<ratio>` | 编译期有理数算术 |
| `<system_error>` | 系统错误支持 |

## 12. 本地化

| 头文件 | 作用 |
|--------|------|
| `<locale>` | 本地化和国际化支持 |
| `<codecvt>` (C++17 弃用) | 字符编码转换 |

## 13. C++20 新特性头文件

| 头文件 | 作用 |
|--------|------|
| `<format>` | 文本格式化库 |
| `<source_location>` | 源代码位置信息 |
| `<syncstream>` | 同步输出流 |
| `<stop_token>` | 线程停止令牌 |
| `<coroutine>` | 协程支持 |

## 14. 其他

| 头文件 | 作用 |
|--------|------|
| `<bit>` (C++20) | 位操作工具 |
| `<filesystem>` (C++17) | 文件系统操作 |
| `<numbers>` (C++20) | 数学常数 |

> **注意**：C++标准库在不同版本中会添加或修改头文件，某些头文件可能在较新版本中已被弃用或移除。
