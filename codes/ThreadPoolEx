## ThreadPoolEx

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <thread>
#include <mutex>
#include <condition_variable>
#include <functional>
#include <future>
#include <atomic>
#include <chrono>

// 一个支持动态扩展线程数和优先级队列的线程池实现
class ThreadPoolEx {
public:
    // 构造函数，初始化线程池并指定初始线程数量
    explicit ThreadPoolEx(size_t initialThreadCount) : stop(false) {
        addWorkers(initialThreadCount); // 创建初始线程数
    }

    // 添加任务到线程池，支持任务结果的返回
    template <class F, class... Args>
    auto enqueue(int priority, F&& func, Args&&... args) 
        -> std::future<typename std::result_of<F(Args...)>::type> {
        
        using ReturnType = typename std::result_of<F(Args...)>::type;

        // 将任务包装成可调用对象并绑定返回结果
        auto task = std::make_shared<std::packaged_task<ReturnType()>>(
            std::bind(std::forward<F>(func), std::forward<Args>(args)...)
        );

        std::future<ReturnType> future = task->get_future();

        {
            std::unique_lock<std::mutex> lock(queueMutex);

            // 将任务和优先级一起存入队列
            tasks.emplace(priority, [task]() { (*task)(); });
        }

        condition.notify_one(); // 通知一个线程执行任务
        return future;          // 返回任务的 future，用于获取结果
    }

    // 动态调整线程池的线程数量
    void resize(size_t newThreadCount) {
        std::unique_lock<std::mutex> lock(queueMutex);

        size_t currentThreadCount = workers.size();
        if (newThreadCount > currentThreadCount) {
            // 增加线程
            addWorkers(newThreadCount - currentThreadCount);
        } else if (newThreadCount < currentThreadCount) {
            // 减少线程
            for (size_t i = 0; i < (currentThreadCount - newThreadCount); ++i) {
                tasks.emplace(-1, [this]() { this->stopThread(); });
            }
        }

        condition.notify_all();
    }

    // 销毁线程池并清理资源
    ~ThreadPoolEx() {
        {
            std::unique_lock<std::mutex> lock(queueMutex);
            stop = true; // 设置停止标志
        }

        condition.notify_all(); // 唤醒所有线程以退出
        for (std::thread& worker : workers) {
            worker.join(); // 等待线程退出
        }
    }

private:
    // 添加多个线程到线程池
    void addWorkers(size_t count) {
        for (size_t i = 0; i < count; ++i) {
            workers.emplace_back([this]() {
                while (true) {
                    std::function<void()> task;
                    {
                        std::unique_lock<std::mutex> lock(this->queueMutex);

                        // 等待任务或线程池停止的通知
                        this->condition.wait(lock, [this]() {
                            return this->stop || !this->tasks.empty();
                        });

                        if (this->stop && this->tasks.empty()) {
                            return; // 线程退出
                        }

                        // 从任务队列取任务（优先级队列的最大值任务）
                        task = std::move(this->tasks.top().second);
                        this->tasks.pop();
                    }

                    try {
                        task(); // 执行任务
                    } catch (const std::exception& ex) {
                        std::cerr << "任务执行出错：" << ex.what() << std::endl;
                    } catch (...) {
                        std::cerr << "任务发生未知错误。" << std::endl;
                    }
                }
            });
        }
    }

    // 停止当前线程
    void stopThread() {
        throw std::runtime_error("Stopping thread");
    }

    std::vector<std::thread> workers;                  // 工作线程容器
    std::priority_queue<std::pair<int, std::function<void()>>> tasks; // 优先级任务队列
    std::mutex queueMutex;                             // 互斥锁，保护任务队列
    std::condition_variable condition;                 // 条件变量，用于线程同步
    std::atomic<bool> stop;                            // 线程池停止标志
};

int main() {
    ThreadPoolEx pool(2); // 创建线程池，初始包含2个线程

    // 向线程池添加多个任务，任务包含优先级（数值越大优先级越高）
    auto result1 = pool.enqueue(1, [] {
        std::this_thread::sleep_for(std::chrono::milliseconds(500));
        std::cout << "低优先级任务完成。" << std::endl;
    });

    auto result2 = pool.enqueue(10, [] {
        std::this_thread::sleep_for(std::chrono::milliseconds(200));
        std::cout << "高优先级任务完成。" << std::endl;
    });

    auto result3 = pool.enqueue(5, [] {
        std::cout << "中优先级任务完成。" << std::endl;
    });

    // 获取任务结果（等待任务完成）
    result1.get();
    result2.get();
    result3.get();

    // 动态调整线程池大小
    pool.resize(4); // 增加线程到4
    std::this_thread::sleep_for(std::chrono::seconds(2));
    pool.resize(1); // 缩减线程到1

    return 0;
}

```
