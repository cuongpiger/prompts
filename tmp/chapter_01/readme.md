1. Sự khác biệt giữa **Spark** và **Hadoop** là:
   * Spark: lưu trữ dữ liệu trên RAM.
   * Hadoop: lưu trữ dữ liệu trên đĩa (HDD, SSD,...).

2. Ngôn ngữ lập trình gốc của **Spark** là Scala.
3. Các khái niệm chính của **Hadoop**:
   * Là một framework cho phép thực hiện các xử lí song song.
   * Có khả năng chịu lỗi trên một cluster.
   * Cung cấp thêm hai thành phần khác là:
     * **HDFS**: lưu trữ phân tán.
     * **MapReduce**: tính toán phân tán.

4. Khái niệm về **HDFS**:
   * Dùng để lưu trữ phân tán và có khả năng chịu lỗi.
   * **NameNode** dùng để phân một file lớn thành các block nhỏ hơn.
   * Kích thước điển hình của một block thường là 64MB hoặc 128MB và nằm rải rác trong cluster.
   * Khả năng chịu lỗi được thực hiện bằng cách sao chép từng block của một file lớn tới một số node trong cluster (mặc định là 3).
   * Nếu một node bị lỗi, thì không thể truy cập được vào các block trên node đó, lúc này các node khác sẽ cung cấp các block trên node bị lỗi này.

5. Khái niệm về **MapReduce**:
    * Là framework hỗ trợ tính toán song song và phân tán của Hadoop.
    * MapReduce cho phép programmer chỉ cần viết một đoạn mã duy nhất nằm gọn bên tròng hàm `map` và hàm `reduce`.
    * Các hàm `map` và `reduce` thực hiện tính toán trên các dataset nằm trên HDFS.
    * Khi chạy chương trình, hàm `map` thực hiện các đoạn mã do programmer viết trên các node. 
    * Hàm `reduce` thì được thực thi trên vài node khác. Sau khi hàm `map` ở các node cho ra kết quả. Các kết quả này sau đó được chuyển đến các node chứa hàm `reduce` và lúc này giai đoạn `reduce` sẽ được thực thi, toàn bộ quá trinh này được gọi là `shuffle`.
    * Tính toán song song ở đây được thực hiện chủ yếu trong giai đoạn `map`.
    * Ở đây, nói Hadoop có khả năng chịu lỗi là vì nếu một node nào đó bị lỗi thì toàn bộ quá trình trên sẽ được thực thi lại ở một node khác.
    * MapReduce được sử dụng ở cả Hadoop và Spark.
    * MapReduce tóm tắt các data trong luồng xử lí của nó thành các cặp key-value. Các bài toán đơn giản như đếm từ thì không sao, tận dụng được khả năng tính toán song song, nhưng các thuật toán như machine learning đòi hỏi quá trình lập đi lập lại thì gặp khó khăn, nên Spark ra đời để giải quyết vấn đề này.
6. Các hạn chế của **Hadoop**:
   * Truy vấn tương tác.
   * Các thuật toán đòi hỏi quá trình lặp lại cao.
7. Các khái niệm về Spark:
   * Được xây dựng dựa trên Hadoop.
   * Dữ liệu được biểu diễn theo Resilient Distribution Dataset (RDD).