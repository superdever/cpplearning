### ThreadPool

```cpp
#include <iostream>
#include <vector>
#include <thread>
#include <queue>
#include <functional>
#include <mutex>
#include <condition_variable>
#include <atomic>

// 线程池类，用于管理和调度多个线程
class ThreadPool {
public:
    // 构造函数，初始化线程池并启动指定数量的线程
    explicit ThreadPool(size_t threadCount) : stop(false) {
        for (size_t i = 0; i < threadCount; ++i) { // 创建指定数量的线程
            workers.emplace_back([this]() { // 使用 lambda 表达式定义每个线程的工作逻辑
                while (true) { // 无限循环，处理任务队列中的任务
                    std::function<void()> task; // 定义一个函数对象，用于保存任务
                    {
                        // 获取队列互斥锁，确保线程安全地访问任务队列
                        std::unique_lock<std::mutex> lock(this->queueMutex);

                        // 等待任务或线程池停止的通知
                        this->condition.wait(lock, [this]() {
                            return this->stop || !this->tasks.empty();
                        });

                        // 如果线程池已停止且任务队列为空，退出循环
                        if (this->stop && this->tasks.empty()) {
                            return;
                        }

                        // 从任务队列中取出一个任务
                        task = std::move(this->tasks.front());
                        this->tasks.pop(); // 从队列中移除该任务
                    }
                    task(); // 执行任务
                }
            });
        }
    }

    // 添加任务到线程池
    template <class F, class... Args>
    void enqueue(F&& func, Args&&... args) {
        {
            std::unique_lock<std::mutex> lock(queueMutex); // 确保任务队列的线程安全

            // 将任务包装成 std::function<void()> 并存入任务队列
            tasks.emplace([func, args...]() {
                func(args...);
            });
        }
        condition.notify_one(); // 通知一个等待中的线程执行任务
    }

    // 析构函数，销毁线程池
    ~ThreadPool() {
        {
            std::unique_lock<std::mutex> lock(queueMutex);
            stop = true; // 设置停止标志
        }
        condition.notify_all(); // 唤醒所有线程，确保线程正常退出
        for (std::thread& worker : workers) {
            worker.join(); // 等待所有线程完成并退出
        }
    }

private:
    std::vector<std::thread> workers;                 // 线程容器，保存所有工作线程
    std::queue<std::function<void()>> tasks;          // 任务队列，用于存储需要执行的任务
    std::mutex queueMutex;                            // 互斥锁，保护任务队列的线程安全
    std::condition_variable condition;                // 条件变量，用于线程间同步
    std::atomic<bool> stop;                           // 是否停止线程池的标志
};

int main() {
    ThreadPool pool(4); // 创建包含4个线程的线程池

    // 向线程池中添加任务
    for (int i = 0; i < 10; ++i) {
        pool.enqueue([i]() {
            std::cout << "Task " << i << " is being processed by thread "
                      << std::this_thread::get_id() << std::endl;
            std::this_thread::sleep_for(std::chrono::milliseconds(500)); // 模拟任务执行
        });
    }

    // 主线程休眠，等待所有任务完成
    std::this_thread::sleep_for(std::chrono::seconds(5));
    std::cout << "All tasks finished." << std::endl;

    return 0;
}


```
