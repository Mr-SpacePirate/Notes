## 0x82 $Thread$ 提供的方法

#### 构造器

- `public Thread(String name)` 可以为当前线程指定名称
- `public Thread(Runnable target)` 封装 $Runnable$ 对象成为线程对象
- `public Thread(Runnable target, String name)` 封装 $Runnable$ 对象成为线程对象，并指定线程名称

#### 方法

- `public void run()` 线程的任务方法
- `public void start()` 启动线程
- `public String getName()` 获取当前线程的名称，线程名称默认是 $Thread-$ 索引
- `public void setName(String name)` 为线程设置名称
- `public static Thread currentThread()` 获取当前执行的线程对象
- `public static void sleep(long time)` 让当前执行的线程休眠多少毫秒后，再继续执行
- `public final void join()...` 让调用当前这个方法的线程先执行完
