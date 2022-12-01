[toc]

# FileOutputStream

```java
    // 如果文件不存在，则创建该文件。前提: 文件的目录存在
    public static void writeFile1() {
        // 创建 FileOutputStream 对象
        FileOutputStream outputStream = null;
        // 创建文件路径
        String filePath = "D:\\JavaCode\\JavaBase\\13-IO\\src\\C3_OutputStream\\demo.txt";
        try {
            outputStream = new FileOutputStream(filePath);
            // write(int byte);
            outputStream.write('H');
            outputStream.write('\n');
            // write(byte[] bytes);
            String string = "Hello, world";
            outputStream.write(string.getBytes());  // string.getBytes(): string -> byte[]
            outputStream.write('\n');
            // write(byte[] bytes, int offset, int length);
            outputStream.write(string.getBytes(), 0, 3);
            // 如果你想要不覆盖前面的内容(追加)，使用 new FileOutputStream(String filePath, boolean append)
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            try {
                outputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
```

