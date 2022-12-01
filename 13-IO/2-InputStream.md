[toc]

# FileInputStrean

```java
    // FileInputStream(String filePath);
    // stream.read(): 每次读取 1 个字节。效率低。
    // 读取到中文字符(3 个字节)，会出现乱码。
    public static void readFile1() {
        String filePath = "D:\\JavaCode\\JavaBase\\13-IO\\src\\C2_InputStream\\demo";
        FileInputStream inputStream = null;
        int read;
        try {
            // 创建 FileInputStream 对象，用于读取文件
            inputStream = new FileInputStream(filePath);
            // 从该输入流读取一个字节的数据。如果没有输入可用，此方法将阻止。
            while ((read = inputStream.read()) != -1) {
                System.out.print(read+ " ");
            }
            System.out.println();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // 关闭 文件流
            try {
                inputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }

    // FileInputStream(String filePath);
    // stream.read(byte[] bytes): 每次读取 1 个字节。效率低。
    public static void readFile2() {
        String filePath = "D:\\JavaCode\\JavaBase\\13-IO\\src\\C2_InputStream\\demo";
        FileInputStream inputStream = null;
        int length;
        byte[] buffer = new byte[3];
        try {
            // 创建 FileInputStream 对象，用于读取文件
            inputStream = new FileInputStream(filePath);
            // 从该输入流读取最多 buffer.length 字节的数据到字节数组。此方法将阻塞，直到某些输入可用。
            // 如果读取正常，返回的是读取到的字节数。
            while ((length = inputStream.read(buffer)) != -1) {
                System.out.print(new String(buffer, 0, length));
            }
            System.out.println();
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // 关闭 文件流
            try {
                inputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
```

