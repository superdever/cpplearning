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

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<iostream>` | 标准输入输出流 | `istream` - 输入流基类<br>`ostream` - 输出流基类<br>`iostream` - 双向流类<br>`cin` - 标准输入流对象<br>`cout` - 标准输出流对象<br>`cerr` - 标准错误流对象(无缓冲)<br>`clog` - 标准日志流对象(有缓冲)<br>`endl` - 插入换行并刷新流<br>`flush` - 刷新流缓冲区 |
| `<fstream>` | 文件流操作 | `ifstream` - 输入文件流类<br>`ofstream` - 输出文件流类<br>`fstream` - 双向文件流类<br>`open(filename, mode)` - 打开文件<br>`close()` - 关闭文件<br>`is_open()` - 检查文件是否打开<br>`read(buf, size)` - 二进制读取<br>`write(buf, size)` - 二进制写入 |
| `<sstream>` | 字符串流操作 | `istringstream` - 输入字符串流类<br>`ostringstream` - 输出字符串流类<br>`stringstream` - 双向字符串流类<br>`str()` - 获取/设置底层字符串<br>`str("content")` - 设置流内容 |
| `<iomanip>` | 流格式控制 | `setw(n)` - 设置字段宽度<br>`setprecision(n)` - 设置浮点精度<br>`setfill(c)` - 设置填充字符<br>`setbase(base)` - 设置数值基数<br>`hex`/`dec`/`oct` - 设置进制<br>`fixed`/`scientific` - 设置浮点格式<br>`boolalpha` - 布尔值字母输出 |
| `<ios>` | 基础流特性 | `ios_base` - 流基类<br>`basic_ios<CharT>` - 模板流基类<br>`good()` - 检查流状态正常<br>`fail()` - 检查流操作失败<br>`eof()` - 检查到达文件尾<br>`clear()` - 清除状态标志 |
| `<iosfwd>` | 流类前向声明 | 包含所有流类的前向声明，用于减少编译依赖 |
| `<istream>` | 输入流操作 | `get()` - 读取单个字符<br>`getline()` - 读取一行<br>`read()` - 读取数据块<br>`ignore(n)` - 跳过n个字符<br>`peek()` - 查看下一个字符<br>`unget()` - 放回字符 |
| `<ostream>` | 输出流操作 | `put(c)` - 写入单个字符<br>`write()` - 写入数据块<br>`flush()` - 刷新缓冲区 |
| `<streambuf>` | 流缓冲区 | `basic_streambuf<CharT>` - 流缓冲区模板类<br>`pubsetbuf()` - 设置缓冲区<br>`sgetc()` - 获取当前字符<br>`sbumpc()` - 获取并前进<br>`sputc(c)` - 放入字符 |

### 典型用法示例

#### 控制台输入输出
```cpp
#include <iostream>
#include <iomanip>

int main() {
    int num;
    std::cout << "Enter a number: ";
    std::cin >> num;
    std::cout << "Hex: " << std::hex << num 
              << " Oct: " << std::oct << num << std::endl;
    std::cout << std::setw(10) << std::setfill('*') << 123 << std::endl;
}
```
文件操作
```cpp
#include <fstream>

// 写入文件
std::ofstream out("data.txt");
out << "Line 1\nLine 2\n";
out.close();

// 读取文件
std::ifstream in("data.txt");
std::string line;
while(std::getline(in, line)) {
    std::cout << line << std::endl;
}
```
字符串流
```cpp
#include <sstream>

std::stringstream ss;
ss << "The answer is " << 42;
std::string s = ss.str();  // "The answer is 42"

int val;
ss >> val;  // 从流中提取数值
```

二进制文件操作
```cpp
#include <fstream>

struct Data { int a; double b; };

// 写入二进制数据
Data d{10, 3.14};
std::ofstream bin_out("data.bin", std::ios::binary);
bin_out.write(reinterpret_cast<char*>(&d), sizeof(d));

// 读取二进制数据
Data d2;
std::ifstream bin_in("data.bin", std::ios::binary);
bin_in.read(reinterpret_cast<char*>(&d2), sizeof(d2));
```
C++的IO流提供了类型安全的输入输出方式，但性能不如C风格的stdio。对于高性能场景，可以考虑：
使用'\n'代替endl避免不必要的刷新
减少格式控制操作
对于大量数据，使用二进制IO
C++20新增的<format>提供了更高效的格式化方式

## 6. 多线程与并发

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<thread>` | 线程支持 | `thread` - 线程类<br>`join()` - 等待线程结束<br>`detach()` - 分离线程<br>`get_id()` - 获取线程ID<br>`sleep_for(dur)` - 线程睡眠指定时长<br>`sleep_until(time)` - 线程睡眠到指定时间<br>`hardware_concurrency()` - 返回硬件线程上下文数量 |
| `<mutex>` | 互斥锁 | `mutex` - 基本互斥锁<br>`lock()` - 获取锁<br>`unlock()` - 释放锁<br>`try_lock()` - 尝试获取锁<br>`recursive_mutex` - 可递归互斥锁<br>`timed_mutex` - 带超时的互斥锁<br>`lock_guard<Mutex>` - RAII锁包装器<br>`unique_lock<Mutex>` - 更灵活的RAII锁包装器 |
| `<shared_mutex>` (C++14) | 共享互斥锁 | `shared_mutex` - 共享互斥锁<br>`lock_shared()` - 获取共享锁<br>`unlock_shared()` - 释放共享锁<br>`shared_lock<Mutex>` - RAII共享锁包装器 |
| `<future>` | 异步操作 | `future<T>` - 异步结果容器<br>`promise<T>` - 存储异步结果<br>`async(fn, args...)` - 异步执行函数<br>`packaged_task<F>` - 打包可调用对象<br>`shared_future<T>` - 可共享的future |
| `<condition_variable>` | 条件变量 | `condition_variable` - 条件变量<br>`wait(lock)` - 等待条件<br>`notify_one()` - 唤醒一个等待线程<br>`notify_all()` - 唤醒所有等待线程<br>`condition_variable_any` - 可与任何锁类型配合的条件变量 |
| `<atomic>` | 原子操作 | `atomic<T>` - 原子类型模板<br>`load()` - 原子加载<br>`store(val)` - 原子存储<br>`exchange(val)` - 原子交换<br>`compare_exchange_strong()` - 比较并交换<br>`atomic_flag` - 原子标志<br>`memory_order` - 内存顺序枚举 |
| `<latch>` (C++20) | 线程同步门闩 | `latch` - 一次性线程屏障<br>`count_down()` - 减少计数<br>`wait()` - 等待计数归零<br>`arrive_and_wait()` - 减少计数并等待 |
| `<barrier>` (C++20) | 线程屏障 | `barrier` - 可重用线程屏障<br>`arrive()` - 到达屏障<br>`wait()` - 等待其他线程<br>`arrive_and_wait()` - 到达并等待<br>`arrive_and_drop()` - 到达并退出 |
| `<semaphore>` (C++20) | 信号量 | `counting_semaphore` - 计数信号量<br>`acquire()` - 获取信号量<br>`release()` - 释放信号量<br>`try_acquire()` - 尝试获取信号量<br>`binary_semaphore` - 二元信号量别名 |

### 典型用法示例

#### 基本线程创建
```cpp
#include <thread>
#include <iostream>

void hello() {
    std::cout << "Hello from thread " 
              << std::this_thread::get_id() << std::endl;
}

int main() {
    std::thread t(hello);
    t.join();  // 等待线程结束
}
```
互斥锁保护共享数据
```cpp
#include <mutex>
#include <thread>

std::mutex mtx;
int shared_data = 0;

void increment() {
    std::lock_guard<std::mutex> lock(mtx);
    ++shared_data;
}
```

异步任务
```cpp
#include <future>
#include <iostream>

int compute() {
    // 长时间计算
    return 42;
}

int main() {
    std::future<int> result = std::async(std::launch::async, compute);
    std::cout << "Result: " << result.get() << std::endl;
}
```
原子操作
```cpp
#include <atomic>
#include <thread>

std::atomic<int> counter(0);

void increment() {
    for (int i = 0; i < 1000; ++i) {
        counter.fetch_add(1, std::memory_order_relaxed);
    }
}
```
C++20信号量
```cpp
#include <atomic>
#include <thread>

std::atomic<int> counter(0);

void increment() {
    for (int i = 0; i < 1000; ++i) {
        counter.fetch_add(1, std::memory_order_relaxed);
    }
}
```
并发编程建议
优先使用高层抽象：

使用async和future而非直接创建线程
使用lock_guard/unique_lock而非手动锁操作
避免数据竞争：
使用互斥锁保护共享数据
考虑使用原子操作实现无锁编程
性能考虑：
减少锁的持有时间
考虑使用读写锁(shared_mutex)优化读多写少场景
使用无锁数据结构提升并发性能
C++20新特性：
latch和barrier简化线程同步
semaphore提供更灵活的同步原语
jthread(joining thread)自动join的线程类型
注意：并发编程容易引入难以调试的问题，建议使用线程分析工具(如TSAN)检查数据竞争和死锁情况。对于复杂并发场景，可以考虑使用更高级的并发库如Intel TBB或Microsoft PPL


## 7. 内存管理

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<memory>` | 智能指针和内存工具 | `shared_ptr<T>` - 共享所有权指针<br>`unique_ptr<T>` - 独占所有权指针<br>`weak_ptr<T>` - 不增加引用计数的观察指针<br>`make_shared<T>(args...)` - 创建shared_ptr<br>`make_unique<T>(args...)` - 创建unique_ptr<br>`allocator<T>` - 标准内存分配器<br>`pointer_traits` - 指针特性模板 |
| `<memory_resource>` (C++17) | 多态内存资源 | `memory_resource` - 抽象内存资源接口<br>`synchronized_pool_resource` - 线程安全的内存池<br>`unsynchronized_pool_resource` - 非线程安全内存池<br>`monotonic_buffer_resource` - 单调缓冲区资源 |
| `<new>` | 动态内存管理 | `operator new` - 全局new运算符<br>`operator delete` - 全局delete运算符<br>`nothrow` - 不抛出异常的new版本<br>`bad_alloc` - 内存分配失败异常<br>`align_val_t` - 对齐类型 |
| `<scoped_allocator>` | 嵌套分配器 | `scoped_allocator_adaptor<Alloc>` - 嵌套分配器适配器<br>`outer_allocator()` - 获取外层分配器<br>`inner_allocator()` - 获取内层分配器 |

### 典型用法示例

#### 智能指针使用
```cpp
#include <memory>

struct Widget {
    int value;
    Widget(int v) : value(v) {}
};

void smart_pointer_demo() {
    auto sp = std::make_shared<Widget>(42);  // 共享指针
    auto up = std::make_unique<Widget>(99);  // 独占指针
    
    std::weak_ptr<Widget> wp = sp;  // 弱指针
    if (auto locked = wp.lock()) {  // 提升为shared_ptr
        // 使用locked
    }
}
```

## 8. 日期与时间

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<chrono>` | 时间库 | `system_clock` - 系统时钟，表示系统范围的实时时钟<br>`now()` - 获取当前时间点<br>`to_time_t()` - 转换为time_t<br>`from_time_t()` - 从time_t转换<br>`steady_clock` - 稳定时钟，适合测量时间间隔<br>`high_resolution_clock` - 高精度时钟（可能是system_clock或steady_clock的别名）<br>`duration<Rep, Period>` - 时间间隔模板类<br>`count()` - 获取时间单位的数量<br>`time_point<Clock, Duration>` - 时间点模板类<br>`time_since_epoch()` - 获取从纪元开始的时间<br>`hours`/`minutes`/`seconds`/`milliseconds`/`microseconds`/`nanoseconds` - 预定义时长类型<br>`duration_cast<D>` - 时长类型转换<br>`floor<D>()` - 向下取整转换<br>`ceil<D>()` - 向上取整转换<br>`round<D>()` - 四舍五入转换 |
| `<date>` (C++20) | 日历日期支持 | `year` - 年类型，表示公历年<br>`month` - 月类型，表示公历月<br>`day` - 日类型，表示公历日<br>`operator/` - 日期字面量语法（如2023y/8/15d）<br>`year_month_day` - 完整日期类型<br>`sys_days` - 系统时钟天数<br>`weekday` - 星期类型<br>`operator[]` - 获取月份的第n个星期几<br>`last` - 表示月份最后一周<br>`time_zone` - 时区信息<br>`zoned_time` - 带时区的时间点 |

### 典型用法示例

#### 时间间隔测量
```cpp
#include <chrono>
#include <thread>
#include <iostream>

void measure_duration() {
    using namespace std::chrono;
    
    auto start = high_resolution_clock::now();
    
    // 模拟耗时操作
    std::this_thread::sleep_for(milliseconds(150));
    
    auto end = high_resolution_clock::now();
    auto elapsed = duration_cast<milliseconds>(end - start);
    
    std::cout << "Elapsed time: " << elapsed.count() << "ms\n";
}
```
时间点转换
```cpp
#include <chrono>
#include <ctime>
#include <iostream>

void time_conversion() {
    using namespace std::chrono;
    
    // 获取当前系统时间
    auto now = system_clock::now();
    
    // 转换为time_t
    std::time_t t = system_clock::to_time_t(now);
    
    // 转换为本地时间字符串
    std::cout << "Current time: " << std::ctime(&t);
}
```
C++20日历日期
```cpp
#include <chrono>
#include <iostream>

void calendar_demo() {
    using namespace std::chrono;
    
    // 创建日期 2023-08-15
    auto date = August/15/2023;
    // 等价于 year_month_day{2023y, August, 15d}
    
    // 获取星期几
    auto weekday = year_month_weekday(date).weekday();
    std::cout << "Weekday: " << weekday << "\n";  // 输出: Tuesday
    
    // 日期运算
    auto next_day = date + days(1);
    auto next_month = date + months(1);
    
    // 格式化输出
    std::cout << "Date: " << date << "\n";  // 输出: 2023-08-15
}
```
带时区的时间(C++20)
```cpp
#include <chrono>
#include <iostream>

void timezone_demo() {
    using namespace std::chrono;
    
    // 获取当前时间点
    auto now = system_clock::now();
    
    // 创建带时区的时间
    auto ny_time = zoned_time{"America/New_York", now};
    auto tokyo_time = zoned_time{"Asia/Tokyo", now};
    
    // 输出不同时区的时间
    std::cout << "New York: " << ny_time << "\n";
    std::cout << "Tokyo: " << tokyo_time << "\n";
}
```
时间处理建议
时钟选择：
使用system_clock获取日历时间
使用steady_clock测量时间间隔（不受系统时间调整影响）
high_resolution_clock可能是前两者的别名
时间单位：
优先使用duration类型而非原始数值
明确时间单位（如seconds, milliseconds）
C++20新特性：
使用<chrono>的日历日期扩展替代旧的<ctime>
zoned_time简化时区处理
日期字面量语法更直观（如2023y/August/15d）
性能考虑：
避免频繁的时钟调用（now()）
对于高频计时，考虑使用steady_clock
注意：C++20的<chrono>扩展大大简化了日期和时间处理，但需要编译器完全支持C++20标准。对于跨平台开发，需检查目标平台的C++20支持情况。



## 9. 类型支持

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<typeinfo>` | 运行时类型信息 | `type_info` - 类型信息类，包含类型的哈希码和名称<br>`typeid(expr)` - 获取表达式的类型信息<br>`before(type_info)` - 类型排序比较<br>`hash_code()` - 获取类型哈希值<br>`name()` - 获取实现定义的类型名称<br>`bad_cast` - dynamic_cast失败时抛出的异常<br>`bad_typeid` - 对空指针应用typeid时抛出的异常 | 
| `<typeindex>` | 类型索引 | `type_index` - 类型索引包装类，可用于关联容器<br>`hash_code()` - 获取类型哈希值<br>`operator==`/`operator<` - 类型比较操作 |
| `<type_traits>` | 类型特性 | `is_void<T>` - 检查是否为void类型<br>`is_integral<T>` - 检查是否为整型<br>`is_floating_point<T>` - 检查是否为浮点型<br>`is_pointer<T>` - 检查是否为指针类型<br>`is_reference<T>` - 检查是否为引用类型<br>`remove_const<T>` - 移除const限定符<br>`add_pointer<T>` - 添加指针修饰<br>`enable_if<B,T>` - 条件启用类型<br>`is_invocable<F,Args...>` - 检查是否可调用<br>`invoke_result<F,Args...>` - 获取调用结果类型 |
| `<limits>` | 数值特性 | `numeric_limits<T>` - 数值类型特性模板<br>`min()` - 返回类型最小值<br>`max()` - 返回类型最大值<br>`lowest()` - 返回类型最小有限值<br>`digits` - 类型位数(不含符号位)<br>`digits10` - 十进制精度位数<br>`is_signed` - 是否为有符号类型<br>`is_integer` - 是否为整数类型<br>`is_exact` - 是否为精确表示 |
| `<variant>` (C++17) | 类型安全联合 | `variant<Types...>` - 类型安全联合模板<br>`index()` - 返回当前存储类型的索引<br>`valueless_by_exception()` - 检查是否因异常丢失值<br>`holds_alternative<T>(v)` - 检查是否存储特定类型<br>`get<T>(v)` - 获取存储的值<br>`get_if<T>(v)` - 获取指向值的指针<br>`visit(visitor, variants...)` - 访问variant值 |
| `<any>` (C++17) | 任意类型容器 | `any` - 可存储任意类型的容器<br>`type()` - 获取存储值的type_info<br>`has_value()` - 检查是否包含值<br>`reset()` - 清空容器<br>`emplace<T>(args...)` - 原位构造值<br>`any_cast<T>(a)` - 转换存储的值 |
| `<optional>` (C++17) | 可选值容器 | `optional<T>` - 可能包含值的容器<br>`value()` - 获取值(无值则抛异常)<br>`value_or(default)` - 获取值或默认值<br>`has_value()` - 检查是否包含值<br>`operator*` - 解引用访问值<br>`operator->` - 成员访问<br>`emplace(args...)` - 原位构造值 |
| `<compare>` (C++20) | 三路比较 | `strong_ordering` - 强序比较结果类型<br>`partial_ordering` - 偏序比较结果类型<br>`weak_ordering` - 弱序比较结果类型<br>`compare_three_way` - 三路比较函数对象<br>`is_eq`/`is_neq`/`is_lt`/`is_lteq`/`is_gt`/`is_gteq` - 比较结果检查 |
| `<concepts>` (C++20) | 概念定义 | `integral` - 检查是否为整型<br>`floating_point` - 检查是否为浮点型<br>`same_as<T,U>` - 检查类型是否相同<br>`derived_from<D,B>` - 检查是否为派生类<br>`convertible_to<T,U>` - 检查是否可转换<br>`invocable<F,Args...>` - 检查是否可调用<br>`predicate<F,Args...>` - 检查是否为谓词 |

### 典型用法示例

#### 类型特性检查
```cpp
#include <type_traits>

template<typename T>
void process(T val) {
    static_assert(std::is_integral_v<T>, 
                 "T must be an integral type");
    if constexpr (std::is_signed_v<T>) {
        // 处理有符号整型
    } else {
        // 处理无符号整型
    }
}
```
variant使用
```cpp
#include <variant>
#include <string>
#include <iostream>

void variant_example() {
    std::variant<int, double, std::string> v = "hello";
    
    std::visit([](auto&& arg) {
        using T = std::decay_t<decltype(arg)>;
        if constexpr (std::is_same_v<T, int>) {
            std::cout << "int: " << arg << "\n";
        } else if constexpr (std::is_same_v<T, double>) {
            std::cout << "double: " << arg << "\n";
        } else if constexpr (std::is_same_v<T, std::string>) {
            std::cout << "string: " << arg << "\n";
        }
    }, v);
}
```
optional使用
```cpp
#include <optional>
#include <iostream>

std::optional<int> divide(int a, int b) {
    if (b == 0) return std::nullopt;
    return a / b;
}

void optional_example() {
    auto result = divide(10, 2);
    if (result) {
        std::cout << "Result: " << *result << "\n";
    } else {
        std::cout << "Division by zero\n";
    }
}
```
三路比较(C++20)
```cpp
#include <compare>
#include <iostream>

void three_way_compare() {
    int a = 5, b = 10;
    auto res = a <=> b;
    
    if (res < 0) {
        std::cout << "a < b\n";
    } else if (res > 0) {
        std::cout << "a > b\n";
    } else {
        std::cout << "a == b\n";
    }
}
```
类型支持建议
编译时类型检查：
使用static_assert和类型特性进行编译时验证
利用if constexpr实现编译时分派
安全类型操作：
优先使用variant替代传统的联合体
使用optional明确表示可能不存在的值
概念约束：
C++20中利用concepts约束模板参数
使用requires子句明确接口要求
类型转换：
使用any_cast进行安全的类型转换
利用visit模式匹配处理variant值
注意：现代C++的类型支持功能大大增强了类型安全性，减少了运行时错误。合理使用这些工具可以编写出更健壮、更易维护的代码。对于复杂的类型操作，建议结合static_assert和概念约束进行充分的编译时检查。

## 10. 异常处理

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<exception>` | 异常基类和工具 | `exception` - 所有标准异常的基类<br>`what()` - 获取异常描述(virtual)<br>`terminate()` - 终止程序处理<br>`set_terminate()` - 设置终止处理函数<br>`uncaught_exceptions()` - 获取未捕获异常计数<br>`terminate_handler` - 终止处理函数类型<br>`bad_exception` - 意外异常时抛出的异常 |
| `<stdexcept>` | 标准异常类 | `logic_error` - 程序逻辑错误基类<br>`runtime_error` - 运行时错误基类<br>`invalid_argument` - 无效参数异常<br>`out_of_range` - 超出范围异常<br>`length_error` - 长度错误异常<br>`range_error` - 区间错误异常<br>`overflow_error` - 算术上溢异常<br>`underflow_error` - 算术下溢异常 |

### 典型用法示例

#### 基本异常处理
```cpp
#include <stdexcept>
#include <iostream>

void process_positive(int num) {
    if (num < 0) {
        throw std::invalid_argument("Number must be positive");
    }
    // 正常处理
}

int main() {
    try {
        process_positive(-5);
    } catch (const std::exception& e) {
        std::cerr << "Error: " << e.what() << std::endl;
        return 1;
    }
    return 0;
}
```
自定义异常类
```cpp
#include <exception>
#include <string>

class MyException : public std::exception {
    std::string msg;
public:
    MyException(const std::string& message) : msg(message) {}
    const char* what() const noexcept override {
        return msg.c_str();
    }
};

void demo() {
    throw MyException("Custom error occurred");
}
```
异常安全资源管理
```cpp
#include <memory>
#include <fstream>

void write_to_file() {
    auto file = std::make_unique<std::ofstream>("data.txt");
    if (!file->is_open()) {
        throw std::runtime_error("Failed to open file");
    }
    
    // 即使抛出异常，unique_ptr也会确保文件关闭
    *file << "Important data\n";
    process_data();  // 可能抛出异常
    
    file->close();
}
```
嵌套异常处理
```cpp
#include <exception>
#include <iostream>

void inner_function() {
    try {
        // 可能抛出异常的代码
    } catch (...) {
        std::throw_with_nested(std::runtime_error("Inner error"));
    }
}

void outer_function() {
    try {
        inner_function();
    } catch (const std::exception& e) {
        std::cerr << "Outer error: " << e.what() << "\n";
        try {
            std::rethrow_if_nested(e);
        } catch (const std::exception& nested) {
            std::cerr << "Nested error: " << nested.what() << "\n";
        }
    }
}
```
异常处理最佳实践
异常使用原则：
使用异常处理异常情况，而非普通控制流
优先使用标准异常类型
自定义异常应继承自std::exception
异常安全保证：
基本保证：不泄露资源，对象处于有效状态
强保证：操作要么完全成功，要么状态回滚
不抛保证：承诺不抛出异常
资源管理：
使用RAII对象管理资源（如智能指针）
确保析构函数不抛出异常
性能考虑：
异常处理机制有开销，不应用于频繁执行的代码路径
在性能关键路径考虑错误码替代方案
现代C++特性：
使用noexcept标记不抛异常的函数
C++17的std::uncaught_exceptions()支持更复杂的资源管理
利用std::terminate()处理不可恢复错误
注意：异常处理是C++错误处理的重要机制，但需要合理使用。对于预期可能发生的错误（如文件不存在），考虑使用错误码或std::optional等其他机制。异常最适合处理那些罕见的、不可预测的错误情况。


## 11. 实用工具

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<utility>` | 通用工具 | `pair<T1,T2>` - 存储两个值的模板类<br>`make_pair(x,y)` - 创建pair对象<br>`move(x)` - 转换为右值引用<br>`forward<T>(x)` - 完美转发<br>`swap(x,y)` - 交换两个值<br>`exchange(x,y)` - 设置新值并返回旧值<br>`integer_sequence<T,Is...>` - 整数序列<br>`index_sequence<Is...>` - 索引序列 |
| `<tuple>` | 元组支持 | `tuple<Ts...>` - 固定大小异构集合<br>`make_tuple(args...)` - 创建tuple对象<br>`get<I>(t)` - 获取第I个元素<br>`tie(args...)` - 创建引用的tuple<br>`tuple_cat(tuples...)` - 连接多个tuple<br>`apply(fn,tuple)` - 将tuple展开为参数调用函数 |
| `<functional>` | 函数对象 | `function<F>` - 通用函数包装器<br>`bind(fn,args...)` - 绑定参数<br>`ref(x)`/`cref(x)` - 创建引用包装器<br>`plus<>`/`minus<>` - 算术函数对象<br>`equal_to<>`/`less<>` - 比较函数对象<br>`hash<T>` - 哈希函数对象<br>`mem_fn(ptr)` - 成员函数指针包装器 |
| `<bitset>` | 位集合 | `bitset<N>` - 固定大小位集合<br>`set(pos)` - 设置位<br>`reset(pos)` - 清除位<br>`flip(pos)` - 翻转位<br>`test(pos)` - 测试位<br>`count()` - 统计设置位数量<br>`to_string()`/`to_ulong()` - 类型转换 |
| `<initializer_list>` | 初始化列表 | `initializer_list<T>` - 初始化列表类<br>`begin()`/`end()` - 迭代器支持<br>`size()` - 元素数量 |
| `<random>` | 随机数生成 | `random_device` - 真随机数生成器<br>`mt19937` - 梅森旋转算法引擎<br>`uniform_int_distribution<>` - 均匀整数分布<br>`normal_distribution<>` - 正态分布<br>`shuffle(beg,end,gen)` - 随机重排元素 |
| `<ratio>` | 编译期有理数 | `ratio<N,D>` - 有理数模板<br>`ratio_add`/`ratio_subtract` - 有理数运算<br>`ratio_less` - 有理数比较 |
| `<system_error>` | 系统错误 | `error_code` - 平台相关错误码<br>`error_category` - 错误类别接口<br>`system_error` - 系统错误异常<br>`generic_category()` - 通用错误类别 |

### 典型用法示例

#### pair和tuple使用
```cpp
#include <utility>
#include <tuple>
#include <iostream>

void tuple_demo() {
    // pair示例
    auto p = std::make_pair(1, "apple");
    std::cout << p.first << ": " << p.second << "\n";
    
    // tuple示例
    auto t = std::make_tuple(3.14, 42, "hello");
    std::cout << std::get<1>(t) << "\n";  // 输出42
    
    // 结构化绑定(C++17)
    auto [x, y, z] = t;
    std::cout << y << "\n";  // 输出42
}
```
函数对象
```cpp
#include <functional>
#include <algorithm>
#include <vector>

void functional_demo() {
    std::vector<int> v{1, 2, 3, 4, 5};
    
    // 使用bind绑定参数
    auto is_greater = std::bind(std::greater<int>(), 
                               std::placeholders::_1, 3);
    int count = std::count_if(v.begin(), v.end(), is_greater);
    
    // 使用lambda表达式
    int sum = 0;
    std::for_each(v.begin(), v.end(), [&sum](int x) {
        sum += x;
    });
}
```
随机数生成
```cpp
#include <random>
#include <iostream>
#include <algorithm>
#include <vector>

void random_demo() {
    // 初始化随机引擎
    std::random_device rd;
    std::mt19937 gen(rd());
    
    // 创建分布
    std::uniform_int_distribution<> dis(1, 6);
    
    // 生成随机数
    for (int i = 0; i < 10; ++i) {
        std::cout << dis(gen) << " ";
    }
    
    // 随机打乱
    std::vector<int> v{1, 2, 3, 4, 5};
    std::shuffle(v.begin(), v.end(), gen);
}
```
系统错误处理
```cpp
#include <system_error>
#include <fstream>
#include <iostream>

void system_error_demo() {
    std::ifstream file("nonexistent.txt");
    if (!file) {
        std::error_code ec(errno, std::generic_category());
        std::cerr << "Error: " << ec.message() << "\n";
        throw std::system_error(ec, "Failed to open file");
    }
}
```
实用工具建议
现代C++特性：
优先使用std::apply处理tuple参数
使用结构化绑定(C++17)简化pair/tuple访问
使用std::invoke(C++17)统一调用各种可调用对象
性能考虑：
std::move和std::forward对性能优化至关重要
随机数引擎应重用而非重复创建
错误处理：
使用std::error_code处理预期可能发生的错误
保留errno值后再进行其他操作
元编程：
std::integer_sequence可用于编译期序列处理
std::ratio支持编译期有理数运算
注意：实用工具头文件提供了许多基础但强大的功能组件。合理使用这些工具可以大幅提升代码质量和开发效率。对于C++17及以上版本，许多实用操作（如结构化绑定）可以进一步简化代码。


## 12. 本地化

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<locale>` | 本地化和国际化支持 | `locale` - 本地化环境类<br>`global(loc)` - 设置全局本地化环境<br>`classic()` - 获取C本地化环境<br>`facet` - 本地化功能基类<br>`ctype<CharT>` - 字符分类和转换facet<br>`num_get<CharT>` - 数值解析facet<br>`num_put<CharT>` - 数值格式化facet<br>`time_get<CharT>` - 时间解析facet<br>`time_put<CharT>` - 时间格式化facet<br>`money_get<CharT>` - 货币解析facet<br>`money_put<CharT>` - 货币格式化facet<br>`messages<CharT>` - 消息目录访问facet |
| `<codecvt>` (C++17 弃用) | 字符编码转换 | `codecvt<InternT,ExternT,State>` - 编码转换facet基类<br>`codecvt_utf8<CharT>` - UTF-8与宽字符转换<br>`codecvt_utf16<CharT>` - UTF-16与宽字符转换<br>`codecvt_utf8_utf16<CharT>` - UTF-8与UTF-16转换<br>`codecvt_mode` - 编码转换模式标志 |

### 典型用法示例

#### 本地化设置
```cpp
#include <locale>
#include <iostream>

void locale_demo() {
    // 设置全局本地化为系统默认
    std::locale::global(std::locale(""));
    
    // 为cout应用本地化
    std::cout.imbue(std::locale());
    
    // 输出本地化格式的数字
    double num = 1234567.89;
    std::cout << "Localized number: " << num << "\n";
    
    // 检查字符分类
    std::locale loc;
    if (std::isalpha('a', loc)) {
        std::cout << "'a' is alphabetic\n";
    }
}
```
编码转换（C++17前）
```cpp
#include <codecvt>
#include <string>
#include <locale>

void codecvt_demo() {
    // UTF-8到UTF-16转换
    std::wstring_convert<std::codecvt_utf8_utf16<wchar_t>> converter;
    std::string utf8 = u8"你好世界";
    std::wstring utf16 = converter.from_bytes(utf8);
    
    // UTF-16到UTF-8转换
    std::string back_to_utf8 = converter.to_bytes(utf16);
}
```
本地化功能说明
locale类：
构造函数接受空字符串表示系统默认本地化
name()方法返回本地化名称字符串
has_facet<T>()检查是否支持特定facet
常用facet：
ctype：字符分类（is(), toupper(), tolower()）
num_get/num_put：数值输入输出格式化
time_get/time_put：时间格式化（get_time(), put_time()）
numpunct：数值标点规则（小数点、千位分隔符）
编码转换注意：
C++17弃用<codecvt>，建议使用第三方库如ICU
替代方案：<locale>的codecvt_byname或平台特定API
最佳实践：
在程序启动时设置全局本地化
为每个流单独设置本地化（imbue()）
对性能敏感场景可缓存facet引用
注意：C++20引入了<format>库提供更好的国际化支持，但完整本地化功能仍需依赖<locale>。字符编码转换在C++17后建议使用第三方库，标准库实现存在平台差异。


## 13. C++20 新特性头文件

| 头文件 | 作用 | 主要类和函数 |
|--------|------|--------------|
| `<format>` | 文本格式化库 | `format(format_str, args...)` - 格式化字符串<br>`format_to(output_it, format_str, args...)` - 格式化输出到迭代器<br>`format_to_n(output_it, n, format_str, args...)` - 带长度限制的格式化<br>`formatted_size(format_str, args...)` - 计算格式化后大小<br>`vformat(format_str, args)` - 使用format_args格式化<br>`format_args` - 格式化参数容器<br>`std::formatter<T>` - 自定义类型格式化特化 |
| `<source_location>` | 源代码位置信息 | `source_location` - 源代码位置类<br>`current()` - 获取当前位置信息<br>`line()` - 获取行号<br>`column()` - 获取列号<br>`file_name()` - 获取文件名<br>`function_name()` - 获取函数名 |
| `<syncstream>` | 同步输出流 | `syncbuf` - 同步缓冲区类<br>`osyncstream` - 同步输出流类<br>`emit()` - 刷新缓冲区并同步<br>`get_wrapped()` - 获取底层流对象 |
| `<stop_token>` | 线程停止令牌 | `stop_token` - 停止令牌(不可变)<br>`stop_source` - 停止信号源<br>`stop_callback` - 停止回调注册<br>`request_stop()` - 请求停止操作<br>`stop_requested()` - 检查是否请求停止<br>`get_token()` - 获取关联的stop_token |
| `<coroutine>` | 协程支持 | `coroutine_handle<Promise>` - 协程句柄<br>`coroutine_traits` - 协程特性<br>`suspend_always` - 总是挂起awaitable<br>`suspend_never` - 从不挂起awaitable<br>`noop_coroutine()` - 创建无操作协程句柄 |

### 典型用法示例

#### 格式化字符串
```cpp
#include <format>
#include <iostream>

void format_demo() {
    std::string message = std::format("Hello, {}! The answer is {}.", "world", 42);
    std::cout << message << std::endl;  // 输出: Hello, world! The answer is 42.
    
    // 格式化数字
    double pi = 3.1415926535;
    std::cout << std::format("{:.2f}", pi) << std::endl;  // 输出: 3.14
}
```
源代码位置
```cpp
#include <source_location>
#include <iostream>

void log(const std::string& message, 
         const std::source_location& loc = std::source_location::current()) {
    std::cout << loc.file_name() << "(" << loc.line() << "): " << message << std::endl;
}

void test() {
    log("Hello from test function");  // 自动捕获调用位置
}
```
同步输出流
```cpp
#include <syncstream>
#include <iostream>
#include <thread>

void syncstream_demo() {
    std::osyncstream sync_out(std::cout);
    
    std::thread t1([&]{
        sync_out << "Hello from " << std::this_thread::get_id() << std::endl;
    });
    
    std::thread t2([&]{
        sync_out << "Hello from " << std::this_thread::get_id() << std::endl;
    });
    
    t1.join();
    t2.join();
    // 输出不会交错
}
```
线程停止令牌
```cpp
#include <stop_token>
#include <thread>
#include <iostream>

void stoppable_thread(std::stop_token token) {
    while (!token.stop_requested()) {
        std::cout << "Working..." << std::endl;
        std::this_thread::sleep_for(std::chrono::seconds(1));
    }
    std::cout << "Stopped!" << std::endl;
}

void stop_token_demo() {
    std::jthread worker(stoppable_thread);
    std::this_thread::sleep_for(std::chrono::seconds(3));
    worker.request_stop();  // 请求停止
}
```
协程基础
```cpp
#include <coroutine>
#include <iostream>

struct Generator {
    struct promise_type {
        int current_value;
        
        Generator get_return_object() {
            return Generator{std::coroutine_handle<promise_type>::from_promise(*this)};
        }
        std::suspend_always initial_suspend() { return {}; }
        std::suspend_always final_suspend() noexcept { return {}; }
        std::suspend_always yield_value(int value) {
            current_value = value;
            return {};
        }
        void return_void() {}
        void unhandled_exception() { std::terminate(); }
    };
    
    std::coroutine_handle<promise_type> coro;
    
    explicit Generator(std::coroutine_handle<promise_type> h) : coro(h) {}
    ~Generator() { if (coro) coro.destroy(); }
    
    int value() { return coro.promise().current_value; }
    bool next() {
        if (!coro.done()) {
            coro.resume();
            return !coro.done();
        }
        return false;
    }
};

Generator range(int from, int to) {
    for (int i = from; i < to; ++i) {
        co_yield i;
    }
}

void coroutine_demo() {
    auto gen = range(1, 5);
    while (gen.next()) {
        std::cout << gen.value() << " ";  // 输出: 1 2 3 4
    }
}
```
C++20新特性建议
格式化优先：
优先使用<format>替代传统printf或字符串拼接
为自定义类型实现formatter特化
协程注意：
协程是栈less的，适合异步I/O等场景
注意协程生命周期管理
编译器支持程度不一，需检查实现
线程控制：
使用stop_token实现优雅的线程停止
jthread(joining thread)自动管理线程生命周期
调试支持：
source_location替代__FILE__和__LINE__宏
适用于日志记录和断言消息
注意：C++20特性需要编译器完全支持，使用时需检查编译器版本和功能支持宏。部分功能如协程在不同编译器中的实现可能有差异。

## 14. 其他

| 头文件              | 作用              | 主要类和函数               |
|---------------------|-------------------|----------------------------|
| `<bit>` (C++20)    | 位操作工具        | - `std::bit_cast`: 安全类型转换工具<br>- `std::has_single_bit`: 检测值是否为单一位<br>- `std::countl_zero`, `std::countl_one`, `std::countr_zero`, `std::countr_one`: 计算位数 |
| `<filesystem>` (C++17) | 文件系统操作    | - `std::filesystem::path`: 表示路径<br>- `std::filesystem::exists`: 检测路径是否存在<br>- `std::filesystem::create_directory`: 创建目录<br>- `std::filesystem::remove`: 删除文件或目录 |
| `<numbers>` (C++20) | 数学常数         | - `std::numbers::pi`: 圆周率常量<br>- `std::numbers::e`: 自然对数常量<br>- `std::numbers::sqrt2`: 平方根常量<br>- `std::numbers::phi`: 黄金比例常量 |

---

### 详细说明：
1. **`<bit>` (C++20)**:
   - **作用**: 提供位操作的工具函数。
   - **主要类和函数**:
     - `std::bit_cast`: 用于安全地将一个对象转换为另一个类型。
     - `std::has_single_bit`: 检查一个值是否只有一位是 `1`。
     - `std::countl_zero`: 计算值前导零的数量。
     - `std::countl_one`: 计算值前导一的数量。
     - `std::countr_zero`: 计算值尾随零的数量。
     - `std::countr_one`: 计算值尾随一的数量。

2. **`<filesystem>` (C++17)**:
   - **作用**: 提供文件系统操作的支持。
   - **主要类和函数**:
     - `std::filesystem::path`: 用于表示路径。
     - `std::filesystem::exists`: 检查路径或文件是否存在。
     - `std::filesystem::create_directory`: 创建新的文件夹。
     - `std::filesystem::remove`: 删除指定文件或目录。

3. **`<numbers>` (C++20)**:
   - **作用**: 提供常见的数学常量。
   - **主要类和函数**:
     - `std::numbers::pi`: 圆周率的值。
     - `std::numbers::e`: 自然对数的底数。
     - `std::numbers::sqrt2`: 平方根常量。
     - `std::numbers::phi`: 黄金比例。


> **注意**：C++标准库在不同版本中会添加或修改头文件，某些头文件可能在较新版本中已被弃用或移除。
