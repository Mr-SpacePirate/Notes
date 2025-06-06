## 0x92 $UDP$ 通信

- 特点：无连接、不可靠通信
- $Java$ 提供了一个 `java.net.DatagramSocket` 类来实现 $UDP$ 通信

### $DatagramSocket$：用于创建客户端、服务端

#### 构造器

- `public DatagramSocket()` 创建**客户端**的 $Socket$ 对象，系统会随机分配一个端口号。
- `public DatagramSocket(int port)` 创建**服务端**的 $Socket$ 对象，并指定端口号。

#### 方法

- `public void send(DatagramPacket dp)` 发送数据包
- `public void receive(DatagramPacket p)` 使用数据包接收数据

### $DatagramPacket$：创建数据包

#### 构造器

- `pulbic DatagramPacket(byte[] buf, int length, InetAddress address, int port)` 创建发出去的数据包对象
- `public DatagramPacket(byte[] buf, int length)` 创建用来接收数据的数据包

#### 方法

- `public int getLength()` 获取数据包，实际接收到的字节个数

### 一收一发

```java
// Client.java
public class Client {
    public static void main(String[] args) throws Exception {
        // 1. 创建客户端对象
        DatagramSocket socket = new DatagramSocket(7777);

        // 2. 创建数据包对象封装要发出去的数据
        byte[] bytes = "hhhhhhhhhh".getBytes();
        DatagramPacket packet = new DatagramPacket(bytes, bytes.length, InetAddress.getLocalHost(), 6666);

        // 3. 开始正式发送这个数据包的数据出去
        socket.send(packet);

        System.out.println("客户端发送完毕");
        socket.close(); // 释放资源
    }
}

// Server.java
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("---服务程序启动---");

        // 1. 创建一个服务端对象
        DatagramSocket socket = new DatagramSocket(6666);

        // 2. 创建一个数据包对象，用于接收数据
        byte[] buffer = new byte[1024 * 64];    // 64kb
        DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

        // 3. 正式用数据包来接收客户端发来的数据
        socket.receive(packet);

        // 4. 从字节数组中，把接收到的数据直接打印出来
        int len = packet.getLength();

        String rs = new String(buffer, 0, len);
        System.out.println(rs);

        System.out.println(packet.getAddress().getHostAddress());
        System.out.println(packet.getPort());

        socket.close();
    }
}

```

### 多收多发

```java
// Client.java
public class Client {
    private static final Scanner sc = new Scanner(System.in);

    public static void main(String[] args) throws Exception {
        // 1. 创建客户端对象
        DatagramSocket socket = new DatagramSocket();

        while (true) {
            System.out.println("请说：");
            String msg = sc.nextLine();

            if (msg.equals("exit")) {
                System.out.println("退出成功，欢迎下次光临");
                socket.close();
                break;
            }

            // 2. 创建数据包对象封装要发出去的数据
            byte[] bytes = msg.getBytes();
            DatagramPacket packet = new DatagramPacket(bytes, bytes.length, InetAddress.getLocalHost(), 6666);

            // 3. 开始正式发送这个数据包的数据出去
            socket.send(packet);
        }
    }
}

// Server.java
public class Server {
    public static void main(String[] args) throws Exception {
        System.out.println("---服务程序启动---");

        // 1. 创建一个服务端对象
        DatagramSocket socket = new DatagramSocket(6666);

        // 2. 创建一个数据包对象，用于接收数据
        byte[] buffer = new byte[1024 * 64];    // 64kb
        DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

        while (true) {
            // 3. 正式用数据包来接收客户端发来的数据
            socket.receive(packet);

            // 4. 从字节数组中，把接收到的数据直接打印出来
            int len = packet.getLength();

            String rs = new String(buffer, 0, len);
            System.out.println(rs);

            System.out.println(packet.getAddress().getHostAddress());
            System.out.println(packet.getPort());
            System.out.println(----------);
        }
    }
}

```