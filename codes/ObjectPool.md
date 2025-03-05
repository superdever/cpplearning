## object pool

```cpp
#include <iostream>
#include <vector>
#include <memory>
#include <mutex>

// 模板类：对象缓冲池
template <typename T>
class ObjectPool {
public:
    // 构造函数，指定缓冲池的初始大小
    explicit ObjectPool(size_t initialSize) {
        for (size_t i = 0; i < initialSize; ++i) {
            pool.emplace_back(std::make_unique<T>()); // 创建对象并存入池中
        }
    }

    // 从池中获取一个对象
    std::shared_ptr<T> acquire() {
        std::unique_lock<std::mutex> lock(poolMutex); // 确保线程安全
        if (!pool.empty()) {
            // 如果池中有可用对象，则取出第一个
            std::shared_ptr<T> obj = std::move(pool.back());
            pool.pop_back(); // 移除该对象
            return obj;
        }

        // 如果池已空，则创建一个新对象
        return std::make_shared<T>();
    }

    // 将对象归还到池中
    void release(std::shared_ptr<T> obj) {
        std::unique_lock<std::mutex> lock(poolMutex); // 确保线程安全
        pool.emplace_back(std::move(obj)); // 将对象放回池中
    }

private:
    std::vector<std::unique_ptr<T>> pool; // 对象池，存储对象
    std::mutex poolMutex;                 // 互斥锁，保护对象池的线程安全
};

// 示例对象
class ExampleObject {
public:
    ExampleObject() {
        std::cout << "ExampleObject Created" << std::endl;
    }

    ~ExampleObject() {
        std::cout << "ExampleObject Destroyed" << std::endl;
    }

    void doWork() {
        std::cout << "Doing work..." << std::endl;
    }
};

int main() {
    ObjectPool<ExampleObject> pool(5); // 创建一个包含5个对象的缓冲池

    // 从缓冲池中获取对象
    auto obj1 = pool.acquire();
    obj1->doWork();

    auto obj2 = pool.acquire();
    obj2->doWork();

    // 将对象归还到缓冲池
    pool.release(obj1);
    pool.release(obj2);

    // 再次获取对象
    auto obj3 = pool.acquire();
    obj3->doWork();

    return 0;
}


```
