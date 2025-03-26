# C++ 标准库头文件列表及作用说明

以下是 C++ 标准库的主要头文件列表及其作用说明（基于 C++20 标准）：

## 1. 标准 C 库头文件（兼容 C）

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<cassert>` | 提供断言宏 | `assert(condition)` - 断言检查，条件为false时终止程序<br>`static_assert(condition, msg)` - 编译期断言检查 |
| `<cctype>` | 字符处理函数 | `isalpha(c)` - 检查字符是否为字母<br>`isdigit(c)` - 检查字符是否为数字<br>`toupper(c)` - 转换为大写字母<br>`tolower(c)` - 转换为小写字母 |
| `<cerrno>` | 错误号宏 | `errno` - 错误号变量<br>`strerror(errno)` - 获取错误描述字符串<br>`perror(msg)` - 打印错误消息 |
| `<cfenv>` | 浮点环境访问 | `fenv_t` - 浮点环境类型<br>`fegetround()` - 获取当前舍入方向<br>`fesetround()` - 设置舍入方向 |
| `<cfloat>` | 浮点数特性宏 | `FLT_MAX` - float类型最大值<br>`DBL_EPSILON` - double类型的机器epsilon<br>`LDBL_DIG` - long double类型的十进制精度位数 |
| `<cinttypes>` | 格式化整数类型 | `int32_t` - 32位有符号整数<br>`uint64_t` - 64位无符号整数<br>`strtoimax(str, endptr, base)` - 字符串转最大宽度整数 |
| `<climits>` | 整数类型特性宏 | `INT_MAX` - int类型最大值<br>`CHAR_BIT` - char的位数(通常为8)<br>`LLONG_MIN` - long long最小值 |
| `<clocale>` | 本地化函数 | `setlocale(category, locale)` - 设置本地化环境<br>`localeconv()` - 获取本地化数字格式信息 |
| `<cmath>` | 数学函数 | `sqrt(x)` - 平方根<br>`sin(x)/cos(x)/tan(x)` - 三角函数<br>`pow(x,y)` - x的y次幂<br>`ceil(x)/floor(x)` - 向上/向下取整 |
| `<csetjmp>` | 非局部跳转 | `jmp_buf` - 跳转缓冲区类型<br>`setjmp(env)` - 设置跳转点<br>`longjmp(env, val)` - 跳转到setjmp点 |
| `<csignal>` | 信号处理 | `signal(sig, handler)` - 设置信号处理函数<br>`raise(sig)` - 发送信号<br>`SIGINT/SIGSEGV` - 信号常量 |
| `<cstdarg>` | 可变参数处理 | `va_list` - 可变参数列表类型<br>`va_start(ap, last)` - 初始化可变参数列表<br>`va_arg(ap, type)` - 获取下一个参数 |
| `<cstddef>` | 基本类型和宏 | `size_t` - 无符号大小类型<br>`NULL` - 空指针常量<br>`offsetof(type, member)` - 成员偏移量 |
| `<cstdio>` | C风格I/O | `FILE` - 文件流类型<br>`printf(format,...)` - 格式化输出<br>`fopen(filename,mode)` - 打开文件<br>`scanf(format,...)` - 格式化输入 |
| `<cstdlib>` | 通用工具 | `malloc(size)` - 内存分配<br>`free(ptr)` - 内存释放<br>`rand()` - 伪随机数生成<br>`exit(status)` - 退出程序 |
| `<cstring>` | 字符串处理 | `strcpy(dest,src)` - 字符串复制<br>`strcmp(s1,s2)` - 字符串比较<br>`memcpy(dest,src,n)` - 内存复制<br>`memset(ptr,val,n)` - 内存设置 |
| `<ctime>` | 时间处理 | `time_t` - 时间类型<br>`time(&timer)` - 获取当前时间<br>`clock()` - 处理器时间<br>`strftime(buf,size,format,tm)` - 时间格式化 |

## 2. 容器相关头文件

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<array>` | 固定大小数组 | `array<T,N>` - 固定大小数组容器<br>`fill(value)` - 填充相同值<br>`at(index)` - 带边界检查的访问 |
| `<vector>` | 动态数组 | `vector<T>` - 动态数组容器<br>`push_back(val)` - 尾部添加元素<br>`reserve(n)` - 预分配内存<br>`emplace_back(args...)` - 原位构造元素 |
| `<deque>` | 双端队列 | `deque<T>` - 双端队列容器<br>`push_front(val)` - 头部插入元素<br>`pop_back()` - 尾部删除元素 |
| `<forward_list>` | 单向链表 | `forward_list<T>` - 单向链表容器<br>`insert_after(pos,val)` - 在指定位置后插入<br>`splice_after(pos,list)` - 转移元素 |
| `<list>` | 双向链表 | `list<T>` - 双向链表容器<br>`sort()` - 链表排序<br>`merge(list)` - 合并有序链表<br>`unique()` - 删除连续重复元素 |
| `<map>` | 关联数组 | `map<K,V>` - 有序键值对容器<br>`operator[key]` - 访问或插入元素<br>`find(key)` - 查找元素<br>`lower_bound(key)` - 返回不小于key的第一个元素 |
| `<set>` | 有序集合 | `set<T>` - 有序集合容器<br>`insert(val)` - 插入元素<br>`count(val)` - 统计元素出现次数<br>`equal_range(val)` - 返回匹配元素范围 |
| `<unordered_map>` | 哈希表实现的map | `unordered_map<K,V>` - 哈希表实现的map<br>`bucket_count()` - 返回桶数量<br>`load_factor()` - 返回负载因子 |
| `<unordered_set>` | 哈希表实现的set | `unordered_set<T>` - 哈希表实现的set<br>`rehash(n)` - 设置桶数量<br>`reserve(n)` - 预留空间 |
| `<stack>` | 栈适配器 | `stack<T>` - 栈容器适配器<br>`push(val)` - 压栈<br>`pop()` - 出栈<br>`top()` - 访问栈顶元素 |
| `<queue>` | 队列适配器 | `queue<T>` - 队列容器适配器<br>`push(val)` - 入队<br>`pop()` - 出队<br>`front()` - 访问队首元素<br>`priority_queue<T>` - 优先队列 |
| `<span>` | 非拥有序列视图 | `span<T>` - 序列视图容器<br>`subspan(offset,count)` - 获取子视图<br>`size()` - 返回元素数量 |


## 3. 算法与迭代器

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<algorithm>` | 通用算法 | `sort(beg, end)` - 排序<br>`find(beg, end, val)` - 查找元素<br>`copy(src_beg, src_end, dest)` - 复制元素<br>`transform(beg, end, dest, op)` - 转换元素 |
| `<execution>` | 并行算法 | `execution::seq` - 顺序执行策略<br>`execution::par` - 并行执行策略<br>`execution::par_unseq` - 并行且向量化执行 |
| `<numeric>` | 数值算法 | `accumulate(beg, end, init)` - 累加<br>`inner_product(beg1, end1, beg2, init)` - 内积<br>`iota(beg, end, value)` - 填充递增序列 |
| `<iterator>` | 迭代器支持 | `back_inserter(container)` - 创建尾部插入迭代器<br>`distance(first, last)` - 计算元素数量<br>`advance(it, n)` - 前进迭代器 |

## 4. 字符串处理

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<string>` | 字符串类型和操作 | `basic_string<CharT>` - 字符串模板类<br>`string` - `basic_string<char>`类型别名<br>`wstring` - `basic_string<wchar_t>`类型别名<br>`to_string(val)` - 将数值转换为字符串<br>`stoi(str)` - 字符串转整数<br>`stod(str)` - 字符串转双精度浮点数<br>`getline(is, str)` - 从输入流读取一行到字符串<br>`str.substr(pos, count)` - 获取子字符串<br>`str.find(substr)` - 查找子字符串位置<br>`str.replace(pos, count, newstr)` - 替换子字符串 |
| `<string_view>` (C++17) | 非拥有字符串视图 | `basic_string_view<CharT>` - 字符串视图模板类<br>`string_view` - `basic_string_view<char>`类型别名<br>`wstring_view` - `basic_string_view<wchar_t>`类型别名<br>`sv.substr(pos, count)` - 获取子视图<br>`sv.find(substr)` - 查找子字符串位置<br>`sv.remove_prefix(n)` - 移除前n个字符<br>`sv.remove_suffix(n)` - 移除后n个字符 |
| `<charconv>` (C++17) | 字符转换 | `to_chars_result` - 转换结果类型<br>`from_chars_result` - 解析结果类型<br>`to_chars(first, last, value)` - 将值转换为字符序列<br>`from_chars(first, last, value)` - 将字符序列解析为值<br>`to_chars(first, last, value, fmt)` - 带格式的转换<br>`from_chars(first, last, value, base)` - 指定基数的解析 |
| `<regex>` | 正则表达式 | `basic_regex<CharT>` - 正则表达式模板类<br>`regex` - `basic_regex<char>`类型别名<br>`wregex` - `basic_regex<wchar_t>`类型别名<br>`match_results` - 匹配结果容器<br>`regex_match(str, re)` - 完全匹配检查<br>`regex_search(str, re)` - 搜索匹配<br>`regex_replace(str, re, fmt)` - 替换匹配内容<br>`sregex_iterator` - 正则搜索迭代器<br>`regex_token_iterator` - 正则分词迭代器 |
### 典型用法示例

#### string 基本操作
```cpp
#include <string>
std::string s = "Hello";
s += " World";  // 字符串拼接
size_t pos = s.find("World");  // 查找子串
std::string sub = s.substr(6, 5);  // 获取子串
int num = std::stoi("42");  // 字符串转整数
```
string_view 使用
```cpp
#include <string_view>
std::string_view sv = "Hello World";
sv.remove_prefix(6);  // sv现在为"World"
size_t pos = sv.find('W');  // 查找字符
```

charconv 数值转换
```cpp
#include <charconv>
char buf[10];
auto [ptr, ec] = std::to_chars(buf, buf+10, 3.1415);  // 高性能转换
double d;
std::from_chars("3.14", "3.14"+4, d);  // 高性能解析
```
正则表达式
```cpp
#include <regex>
std::regex re(R"(\d+)");  // 匹配数字
bool match = std::regex_match("123", re);  // 完全匹配检查
std::string s = std::regex_replace("a1b2", re, "-");  // 替换为"-"
```
字符串处理是C++中最常用的功能之一，现代C++(C++17以后)推荐使用string_view代替const string&参数，使用charconv代替传统的字符串转换函数以获得更好性能。正则表达式功能强大但性能开销较大，适合复杂模式匹配场景。

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
