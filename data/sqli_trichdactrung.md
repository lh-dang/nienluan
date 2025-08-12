# Trích đặc trưng văn bản có 3 loại chính 
1. Dựa trên tần suất từ
- Bag of Words (BoW): Đếm số lần từ xuất hiện.
- TF-IDF: Đếm nhưng có trọng số để giảm ảnh hưởng từ quá phổ biến.
2. Dựa trên biểu diễn phân tán (word embeddings)
- Word2Vec, GloVe, FastText: Mỗi từ là một vector, giữ ngữ nghĩa.
3. Dựa trên mô hình ngôn ngữ hiện đại
- BERT, GPT embeddings: Lấy đặc trưng từ mô hình học sâu, giữ cả ngữ nghĩa và ngữ cảnh.

## 1. Dựa trên tần suất từ
### **Bag of Words (BoW) – Túi từ**
- **Nguyên lý:** Xem văn bản như một “túi” chứa các từ, không quan tâm đến thứ tự, chỉ quan tâm số lần từ xuất hiện.
- **Ưu điểm:** Đơn giản, dễ triển khai, hiệu quả với văn bản ngắn.
- **Nhược điểm:** Không hiểu ngữ cảnh, từ “DROP” và “DROPED” sẽ được coi là 2 từ khác nhau.

### N-grams
- **Nguyên lý:** Thay vì tách từng từ đơn, nó ghép n từ liên tiếp thành một đặc trưng.
- Ví dụ với n=2 (bigram):
`"SELECT * FROM users" → ("SELECT *", "* FROM", "FROM users")`
- **Tác dụng:**
  - Giữ được một phần thứ tự từ.
  - Bắt được các mẫu đặc trưng như "UNION SELECT", "DROP TABLE".
- **Nhược điểm:** Từ điển phình to rất nhanh khi n tăng.

### TF-IDF (Term Frequency – Inverse Document Frequency)
- **Nguyên lý:**
  - TF: Tần suất từ xuất hiện trong tài liệu.
  - IDF: Giảm trọng số của những từ xuất hiện quá nhiều trong toàn bộ tập dữ liệu (ví dụ: "SELECT", "FROM").
  - Công thức:
```
TF-IDF = TF × log(N / DF)
```
  - N: Số tài liệu.
  - DF: Số tài liệu chứa từ đó.
- **Ưu điểm:** Loại bỏ ảnh hưởng từ phổ biến, giữ từ đặc trưng.
- **Nhược điểm:** Vẫn không hiểu ngữ cảnh, chỉ cải thiện so với BoW.
### CountVectorizer với ký tự (Character-level)
- **Nguyên lý:** Không đếm theo từ mà đếm theo chuỗi ký tự liên tiếp (n-gram ký tự).
- Ví dụ:
`"SELECT" với 3-gram ký tự → "SEL", "ELE", "LEC", "ECT".`
- Ứng dụng: Tốt cho phát hiện tấn công SQLi vì bắt được chuỗi như '--, /*, UNION, OR 1=1.
