## 0x93 $TCP$ 通信

- 特点：面向连接、可靠通信
- $Java$ 提供了一个 `java.net.Socket` 类来实现 $TCP$ 通信

### 客户端开发

#### $Socket$ 类

##### 构造器

- `public Socket(String host, int port)` 根据指定的服务器 $ip$、端口号请求与服务端建立连接，连接通过，就获得了客户端 $socket$

##### 方法

- `public OutputStream getOutputStream()` 获得字节输出流对象
- `public InputStream getInputStream()` 获得字节输入流对象

### 服务端开发

#### $ServerSocket$ 类

##### 构造器

- `public ServerSocket(int port)` 为服务程序注册端口

##### 方法

- `public Socket accept()` 阻塞等待客户端的连接请求，一旦与某个客户端连接成功，则返回服务端这边的 $Socket$ 对象。

### 一收一发

```java
// Client.java
public class Client {
    private static final Scanner sc = new Scanner(System.in);

    public static void main(String[] args) throws Exception {
        // 1. 创建Socket对象，同时请求与服务端程序的连接
        Socket socket = new Socket("127.0.0.1", 8888);

        // 2. 从Socket通信管道中得到一个字节输出流，用来发数据给服务端程序
        OutputStream os = socket.getOutputStream();

        // 3. 把低级的字节输出流包装成数据输出流
        DataOutputStream dos = new DataOutputStream(os);

        // 4. 开始写数据出去
        dos.writeUTF("Hello World!");
        dos.close();
        socket.close(); // 释放连接资源
    }
}

// Server.java
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("---服务程序启动---");

        // 1. 创建一个服务端对象，同时为服务端注册端口
        ServerSocket serverSocket = new ServerSocket(8888);

        // 2. 使用serverSocket对象，调用一个accept方法，等待客户端的连接请求
        Socket socket = serverSocket.accept();

        // 3. 从socket通信管道中得到一个字节输入流
        InputStream is = socket.getInputStream();

        // 4. 把原始的字节输入流包装成数据输入流
        DataInputStream dis = new DataInputStream(is);

        // 5. 使用数据输入流读取客户端发送过来的信息
        String rs = dis.readUTF();
        System.out.println(rs);

        // 可以获取客户端ip地址
        System.out.println(socket.getRemoteSocketAddress());

        dis.close();
        socket.close();
    }
}
```

### 多发多收

```java
// Client.java
public class Client {
    private static final Scanner sc = new Scanner(System.in);

    public static void main(String[] args) throws Exception {
        // 1. 创建Socket对象，同时请求与服务端程序的连接
        Socket socket = new Socket("127.0.0.1", 8888);

        // 2. 从Socket通信管道中得到一个字节输出流，用来发数据给服务端程序
        OutputStream os = socket.getOutputStream();

        // 3. 把低级的字节输出流包装成数据输出流
        DataOutputStream dos = new DataOutputStream(os);

        while (true) {
            System.out.println("请说：");
            String msg = sc.nextLine();

            if (msg.equals("exit")) {
                System.out.println("退出成功，欢迎下次光临");
                dos.close();
                socket.close();
                break;
            }

            // 4. 开始写数据出去
            dos.writeUTF(msg);
            dos.flush();
        }
    }
}

// Server.java
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("---服务程序启动---");

        // 1. 创建一个服务端对象，同时为服务端注册端口
        ServerSocket serverSocket = new ServerSocket(8888);

        while (true) {
            // 2. 使用serverSocket对象，调用一个accept方法，等待客户端的连接请求
            Socket socket = serverSocket.accept();

            // 上线提示
            System.out.println(socket.getRemoteSocketAddress() + "上线了！");

            // 3. 把这个客户端对应的socket通信管道，交给一个独立的线程负责处理
            new ServerReaderThread(socket).start();
        }
    }
}

// ServerReaderThread.java
public class ServerReaderThread extends Thread {

    private final Socket socket;

    public ServerReaderThread(Socket socket) {
        this.socket = socket;
    }

    @Override
    public void run() {
        try {
            InputStream is = socket.getInputStream();
            DataInputStream dis = new DataInputStream(is);
            while (true) {
                try {
                    // 接收信息，并打印
                    String msg = dis.readUTF();
                    System.out.println(msg);
                } catch (IOException e) {
                    // 下线提示
                    System.out.println(socket.getRemoteSocketAddress() + "下线了！");
                    dis.close();
                    socket.close();
                    break;
                }
            }
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }
}
```